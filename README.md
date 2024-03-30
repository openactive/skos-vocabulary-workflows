# skos-vocabulary-workflows
These publishing workflows are used by all OpenActive SKOS Vocabularies.

## create-and-merge-pr.yaml

This workflow is triggered by the `skos-vocabulary-editor`. It retrieves the latest SKOS vocabulary from the relevant instance of the editor as a Zip file containing JSON-LD, and then extracts it into a PR if it contains any changes. It also sets this PR to auto-merge if validation (see below) is successful.

## validate-and-release.yaml

This workflow runs on every PR to validate the JSON-LD SKOS file, to guarantee its format and integrity (using the JSON Schema file within this repository).

The workflow also runs on the `main` branch, to first validate as above, and then create a new GitHub Release containing the vocabulary, as well as publishing it via GitHub pages.

Note the use of `.gitattributes` within the OpenActive SKOS Vocabulary repositories to ensure that these releases only include the SKOS data files and do not include other code or documentation.

Note also the `index.hbs` file in this repository that is outputted as `index.html` to GitHub Pages, and allows the `@id`s of the `Concept`s within the vocabularies to resolve to the relevant page within the appropriate `skos-vocabulary-editor`.