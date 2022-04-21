<walkthrough-metadata>
  <meta name="title" content="Recommendations. Import catalog data"/>
  <meta name="description" content="This tutorial shows you how to prepare the catalog to create the recommendation model." />
  <meta name="component_id" content="593554" />
  <meta name="short_id" content="true" />
</walkthrough-metadata>

## Get started

This tutorial shows you how to prepare the catalog data, such as prodcuts and user events, to create the recommendation model.

<walkthrough-tutorial-duration duration="10"></walkthrough-tutorial-duration>

<<_shared/_set_up_env_python.md>>

## Import catalog data

<i>This step is required if this is the first Retail API tutorial that you run.
Otherwise, you can skip it.</i>

There is a <walkthrough-editor-select-regex filePath="cloudshell_open/nodejs-retail/samples/interactive-tutorials/resources/<...products.json>" regex="id">resources/<...products.json></walkthrough-editor-select-regex> file with valid products prepared in the `resources` directory.

The other file, <walkthrough-editor-select-regex filePath="cloudshell_open/nodejs-retail/samples/interactive-tutorials/resources/<...events.json>" regex="id">resources/<...events.json></walkthrough-editor-select-regex>, contains valid user events.

- If you want to **speed up the process**, run the following script in the Terminal from **cloudshell_open/nodejs-retail/samples** directory to import all products and historical user events to the catalog and skip the next **Prepare the catalog data step-by-step** tutorial step:

    ```bash
    bash ~/cloudshell_open/nodejs-retail/samples/interactive-tutorials/recommendations_import_data_to_catalog.sh
    ```

- If you want to upload products and historical user events to the catalog step-by-step along with getting the explanation, you should proceed with the next tutorial step.

## Prepare the catalog data step-by-step

### Upload catalog data to Cloud Storage

In your own project you need to create a Cloud Storage bucket and put the JSON file there.
The bucket name must be unique. For convenience, you can name it `<YOUR_PROJECT_ID>_<TIMESTAMP>`.

1. To create the bucket and upload both <...products.json> and <...events.json> files, open <walkthrough-editor-select-regex filePath="cloudshell_open/nodejs-retail/samples/interactive-tutorials/setup/recommendations-create-gcs-bucket.js" regex="generatedBucketName">setup/recommendations-create-gcs-bucket.js</walkthrough-editor-select-regex> file

1. Run the following command in the Terminal:

    ```bash
    node interactive-tutorials/setup/recommendations-create-gcs-bucket.js
    ```

    Now you can see the bucket is created in the [Cloud Storage](https://console.cloud.google.com/storage/browser), and the files are uploaded.

1. The name of the created Cloud Storage bucket is shown in the Terminal.

    ```
    The gcs bucket <YOUR_PROJECT_ID>_<TIMESTAMP> was created
    ```

    Copy the name and set it as the environment variable `RECOMMENDATIONS_BUCKET_NAME`:

    ```bash
    export RECOMMENDATIONS_BUCKET_NAME=<YOUR_BUCKET_NAME>
    ```

### Import products and user events to the Retail Catalog

To import the prepared products to a catalog, open <walkthrough-editor-select-regex filePath="cloudshell_open/nodejs-retail/samples/interactive-tutorials/product/import-products-gcs.js" regex="node product/import-products-gcs.js">product/import-products-gcs.js</walkthrough-editor-select-regex> file and run the following command in the Terminal:

```bash
node interactive-tutorials/product/recommendations_import_data_to_catalog.js
```

## Your Retail catalog is ready to use!

If you have chosen to set up the envoronment and the catalog data using **bash script**, before run the code sample you should:
- Change the current directory to the **interactive-tutorials** - the starting point for all code samples.
- Set the **`GOOGLE_APPLICATION_CREDENTIALS`** environment variable for current shell session.

To do that, run the following command in a Terminal:

```bash
export GOOGLE_APPLICATION_CREDENTIALS=~/key.json
cd ~/cloudshell_open/nodejs-retail/samples/interactive-tutorials
```

Next, proceed with the second part of the Prediction tutorials: Creating and training the recommendation model.<... link to video>
