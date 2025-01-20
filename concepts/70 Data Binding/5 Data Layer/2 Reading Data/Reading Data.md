For simplicity, this section uses an [in-memory array](/concepts/70%20Data%20Binding/5%20Data%20Layer/1%20Creating%20DataSource/0%20From%20Array.md '/Documentation/Guide/Data_Binding/Data_Layer/#Creating_DataSource/From_Array') to explain data reading:

    <!--JavaScript-->
    const dataSource = new DevExpress.data.DataSource([
        { name: "item1" },
        { name: "item2" },
        { name: "item3" }
    ]);

This section applies to any data source.

To load data, call the [dataSource.load()](/api-reference/30%20Data%20Layer/DataSource/3%20Methods/load().md '/Documentation/ApiReference/Data_Layer/DataSource/Methods/#load') method.

    <!--JavaScript-->
    dataSource.load()
        .done(function(result) {
            // 'result' contains the array associated with the DataSource
        })
        .fail(function(error) {
            // handle error
        });

The [DataSource](/api-reference/30%20Data%20Layer/DataSource '/Documentation/ApiReference/Data_Layer/DataSource/') allows you to specify initial data shaping properties (sort, filter, etc.).

    <!--JavaScript-->
    const dataSource = new DevExpress.data.DataSource({
        store: [
            { name: "Charlie", value: 10 },
            { name: "Alice", value: 20 },
            { name: "Bob", value: 30 }
        ],
        filter: [ "value", ">", 15 ],
        sort: { field: "name", desc: true }
    });

In the [ArrayStore](/api-reference/30%20Data%20Layer/ArrayStore '/Documentation/ApiReference/Data_Layer/ArrayStore/'), [LocalStore](/api-reference/30%20Data%20Layer/LocalStore '/Documentation/ApiReference/Data_Layer/LocalStore/'), and [ODataStore](/api-reference/30%20Data%20Layer/ODataStore '/Documentation/ApiReference/Data_Layer/ODataStore/') data shaping operations are applied in the following order: 

1. [Filtering](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/15%20Filtering '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Filtering')
2. [Sorting](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/1%20Sorting.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Sorting')
3. [Selection](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/3%20Data%20Transformation/0%20Select%20Expressions.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Data_Transformation/Select_Expressions')
4. [Grouping](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/4%20Grouping.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Grouping')
5. [Paging](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/0%20Paging.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Paging')
6. [Item mapping](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/3%20Data%20Transformation/1%20Item%20Mapping.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Data_Transformation/Item_Mapping')
7. [Post processing](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/3%20Data%20Transformation/2%20Post%20Processing.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Data_Transformation/Post_Processing').

The [CustomStore](/api-reference/30%20Data%20Layer/CustomStore '/Documentation/ApiReference/Data_Layer/CustomStore/') passes data shaping properties to the [load(options)](/api-reference/30%20Data%20Layer/CustomStore/3%20Methods/load(options).md '/Documentation/ApiReference/Data_Layer/CustomStore/Methods/#loadoptions') method. This method allows you to process these properties in any required order.
