# EditionCrafter Demo 

This project provides a simple Astro app that serves an EditionCrafter viewer component. To run it locally, first install its dependencies:

`npm install`

You will also want to install the EditionCrafter CLI:

`npm install -g @cu-mkp/editioncrafter-cli`


## Adding Your Edition

First, use the EditionCrafter CLI to create the artifacts EditionCrafter needs. You will need a TEI/XML file that meets EditionCrafter's requirements (https://cu-mkp.github.io/editioncrafter/getting-started/) 

Run the following command:

`editioncrafter process my-edition.xml public http://localhost:4321`

Next, you will need to configure the EditionCrafter viewer to point at the artifacts you just generated. Edit the properties of the `<EditionCrafter>` component in `src/pages/index.astro`.

```
<EditionCrafter
    documentName='MY EDITION NAME'
    transcriptionTypes={{
        translation: 'Translation',
        transcription: 'Transcription',
    }}
    iiifManifest='https://locahost:4321/my-edition/iiif/manifest.json'
    client:only
/>
```

Please note that this configuration assumes you have two textual layers, one called transcription and the other called translation. Please see the EditionCrafter documentation for information on how to configure your edition's layers: https://cu-mkp.github.io/editioncrafter/getting-started/#editing-a-document

## Running EditionCrafter Demo Locally

Once you have added your edition using the steps above, start a local Astro server to view it:

`npm run dev`
