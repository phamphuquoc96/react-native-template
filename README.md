React-Native-Template
================================================
The goal of this project is to work as template for react-native applications, providing a base project structure, core dependencies and boilerplate to jumpstart development.

## Prerequisites
- [Node JS > 12](https://nodejs.org/) and npm (Recommended: Use [nvm](https://github.com/nvm-sh/nvm))
- [Watchman](https://facebook.github.io/watchman/)
- [Xcode](https://developer.apple.com/xcode/)
- [Cocoapods](https://cocoapods.org/)
- [JDK > 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- [Android Studio and Android SDK](https://developer.android.com/studio/index.html)


## Base dependencies
- [Axios](https://github.com/axios/axios) for networking.
- [PropTypes](https://github.com/facebook/prop-types) to type-check our components exposed properties.
- [React-Native-Config](https://github.com/luggit/react-native-config) to manage envionments.
- [React-Navigation](https://reactnavigation.org/) navigation library.
- [React-Native-Localization](https://github.com/stefalda/ReactNativeLocalization) for string localization.
- [Redux](https://redux.js.org/) for state management.
- [Redux-Persist](https://github.com/rt2zz/redux-persist) as persistance layer.
- [Redux-Thunk](https://github.com/gaearon/redux-thunk) to dispatch asynchronous actions.
- [Jest](https://facebook.github.io/jest/) and [React-Native-Testing-Library](https://callstack.github.io/react-native-testing-library/) for testing.

## Usage

#### Use Template button
Click the "Use this template" button above the file list, then use the Owner drop-down menu, and select the account you want to own the repository. Creating a repository from a template has the following advantages:

- A repository created from a template starts with a single commit.
- Commits to a repository created from a template do appear in your contribution graph.
- Creating a repository from a template starts a new project quickly.

### Option #1: Using React-Native-Rename
You can start by cloning this repository and using [react-native-rename](https://github.com/junedomingo/react-native-rename). In the current state of this project, it should give you no issues at all, just run the script, delete your node modules and reinstall them and you should be good to go.

Keep in mind that this library can cause trouble if you are renaming a project that uses `Pods` on the iOS side.

After that you should proceed as with any javascript project:
- Go to your project's root folder and run `npm install`.
- Create a `.env` file to store all your configuration constants. Remember to not commit this file, since it can store sensible information of your product.
- Run `npm run ios` or `npm run android` to start your application!

### Option #2: Copy the structure to your project
If you want to roll on your own and don't want to use this as a template, you can create your own project and then copy the `/src` folder (which has all the code of your application) and update your `index.js`.

Keep in mind that if you do this, you'll have to **install and link** all dependencies (as well as adding all the necessary native code for each library that requires it).

## Folder structure
This template follows a very simple project structure:
- `src`: This folder is the main container of all the code inside your application.
  - `actions`: This folder contains all actions that can be dispatched to redux.
  - `assets`: Asset folder to store all images, vectors, etc.
  - `components`: Folder that contains all your application components.
    - `common`: Folder to store any common component that you use through your app (such as a generic button, textfields, etc).
    - `MyComponent`: Each component should be stored inside it's own folder, and inside it a file for its code and a separate one for the styles. Then, the `index.js` is only used to export the final component that will be used on the app.
      - `MyComponent.js`
      - `styles.js`
      - `index.js`
  - `constants`: Folder to store any kind of constant that you have.
  - `controllers`: Folder to store all your network and storage logic (you should have one controller per resource).
  - `helpers`: Folder to store any kind of helper that you have.
  - `localization`: Folder to store the languages files.
  - `navigation`: Folder to store the navigators.
  - `reducers`: This folder should have all your reducers, and expose the combined result using its `index.js`
  - `selectors`: Folder to store your selectors for each reducer.
  - `store`: Folder to put all redux middlewares and the store.
  - `App.js`: Main component that starts your whole app.
- `index.js`: Entry point of your application as per React-Native standards.

## Splash screen customization

To customize the splash screen (logo and background color) use the CLI provided in the [official docs](https://github.com/zoontek/react-native-bootsplash#assets-generation).

## Setup environments
Add the environment variables files in root folder(.env.staging and .env.production)

#### Android

A map associating builds with env files is already defined in `app/build.gradle` you can modify or add environments if needed.

#### iOS

The basic idea in iOS is to have one scheme per environment file, so you can easily alternate between them.

Start by creating a new scheme:

- In the Xcode menu, go to Product > Scheme > Edit Scheme
- Click Duplicate Scheme on the bottom
- Give it a proper name on the top left. For instance: "Production"
- Then edit the newly created scheme to make it use a different env file. From the same "manage scheme" window:

Expand the "Build" settings on left
- Click "Pre-actions", and under the plus sign select "New Run Script Action"
- Where it says "Type a script or drag a script file", type: `echo ".env.production" > /tmp/envfile` replacing .env.production with your file

## Styleguide
For coding styling we decided to go with ESLint and [Airbnb's styleguide](https://github.com/airbnb/javascript) with a few exceptions that you can find on the [.eslintrc](./.eslintrc)
