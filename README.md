![logo](logo.png)

this is a sample application that demonstrates how to build applications with CD/CI and integrate with Salesforce Experiences.

## Table of contents

-   [Installing base proyect using a scratch org](#installing-base-proyect-using-a-scratch-org)

-   [Installing base proyect a Developer Edition Org or a Trailhead Playground](#installing-base proyect-using-a-developer-edition-org-or-a-trailhead-playground)

-   [Optional installation instructions](#optional-installation-instructions)

-   [Code tours](#code-tours)

## Installing base proyect using a Scratch Org

1. Set up your environment. Follow the steps in the [Quick Start: Lightning Web Components](https://trailhead.salesforce.com/content/learn/projects/quick-start-lightning-web-components/) Trailhead project. The steps include:

    - Enable Dev Hub in your Trailhead Playground
    - Install Salesforce CLI
    - Install Visual Studio Code
    - Install the Visual Studio Code Salesforce extensions, including the Lightning Web Components extension

1. If you haven't already done so, authorize your hub org and provide it with an alias (**myhuborg** in the command below):

    ```
    sfdx auth:web:login -d -a myhuborg
    ```

1. Clone the repository:

    ```
    git clone https://github.com/sergiobaca/serieslexCDCI
    cd proyectobase
    ```

1. Create a scratch org and provide it with an alias (**serieslex** in the command below):

    ```
    sfdx force:org:create -s -f config/project-scratch-def.json -a serieslex
    ```

1. Push the app to your scratch org:

    ```
    sfdx force:source:push
    ```

1. Assign the **CORE** permission set to the default user:

    ```
    sfdx force:user:permset:assign -n CORE
    ```

1. Import sample data:

    ```
    sfdx force:data:tree:import -p ./data/sample-data-plan.json
    ```

1. Open the scratch org:

    ```
    sfdx force:org:open
    ```

## InstallingSerieslex using a Developer Edition Org or a Trailhead Playground

Follow this set of instructions if you want to deploy the app to a more permanent environment than a Scratch org.
This includes non source-tracked orgs such as a [free Developer Edition Org](https://developer.salesforce.com/signup) or a [Trailhead Playground](https://trailhead.salesforce.com/).

Make sure to start from a brand-new environment to avoid conflicts with previous work you may have done.

1. Clone this repository:

    ```
    git clone https://github.com/sergiobaca/serieslexCDCI
    cd serieslexCDCI
    ```

1. Authorize your Trailhead Playground or Developer org and provide it with an alias (**mydevorg** in the command below):

    ```
    sfdx auth:web:login -s -a mydevorg
    ```

1. Start an In-App Guidance trial

    1. In Setup, navigate to **User Engagement > In-App Guidance**.
    1. Click on the **Start Walkthrough Trial**.
    1. Click on **Submit**.

1. Deploy the App with these steps:

    1. Run this command in a terminal to deploy the app.

        ```
        sfdx force:source:deploy -p force-app
        ```

1. Assign the **CORE** permission set to the default user:
     1. Run this command in a terminal to deploy the app.
        ```
        sfdx force:user:permset:assign -n CORE
        ```

    1. Import some sample data.

        ```
        sfdx force:data:tree:import -p ./data/sample-data-plan.json
        ```

    1. If your org isn't already open, open it now:

        ```
        sfdx force:org:open -u mydevorg
        ```

## Optional Installation Instructions

This repository contains several files that are relevant if you want to integrate modern web development tooling to your Salesforce development processes, or to your continuous integration/continuous deployment processes.

### Code formatting

[Prettier](https://prettier.io/) is a code formatter used to ensure consistent formatting across your code base. To use Prettier with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) from the Visual Studio Code Marketplace. The [.prettierignore](/.prettierignore) and [.prettierrc](/.prettierrc) files are provided as part of this repository to control the behavior of the Prettier formatter.

### Code linting

[ESLint](https://eslint.org/) is a popular JavaScript linting tool used to identify stylistic errors and erroneous constructs. To use ESLint with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode-lwc) from the Visual Studio Code Marketplace. The [.eslintignore](/.eslintignore) file is provided as part of this repository to exclude specific files from the linting process in the context of Lightning Web Components development.

### Pre-commit hook

This repository also comes with a [package.json](./package.json) file that makes it easy to set up a pre-commit hook that enforces code formatting and linting by running Prettier and ESLint every time you `git commit` changes.

To set up the formatting and linting pre-commit hook:

1. Install [Node.js](https://nodejs.org) if you haven't already done so

1. Run `npm install` in your project's root folder to install the ESLint and Prettier modules (Note: Mac users should verify that Xcode command line tools are installed before running this command.)

Prettier and ESLint will now run automatically every time you commit changes. The commit will fail if linting errors are detected. You can also run the formatting and linting from the command line using the following commands (check out [package.json](./package.json) for the full list):

```
npm run lint:lwc
npm run prettier
```

## Code Tours

Code Tours are guided walkthroughs that will help you understand the app code better. To be able to run them, install the [CodeTour VSCode extension](https://marketplace.visualstudio.com/items?itemName=vsls-contrib.codetour).
