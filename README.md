# node-expressjs-sequelize-2016

A boilerplate using NodeJs, Express, Sequelize, Apidoc, Eslint, Mocha, Cluster and the best practices.

## Getting up and running

1. Clone the repository
2. `npm install`
3. `npm start`
4. Visit `https://localhost:3000`
5. Visit `https://localhost:3000/apidoc` to see the existing API (under construction)

## Some command

```
npm start  # Run the serveur in cluster mode (it also generate the apidoc)
npm lint   # Check lint error using eslint
npm test   # run mocha tests  // npm install mocha
npm apidoc # Generate the apidoc // npm install apidoc -g
```

## Coding Style

The coding style used is the spheria style.

You can configure it in the `.eslintrc` file.

## Architecture

The architecture is MVC (Model View Controller)

The files are structured in the following manner:
```
libs        (Configurations files and libs)
models      (Sequelize models)
routes      (Express routes, the comments in this folder are used to generate the apidoc)
test        (mocha test, 'npm test' to run it)
auth.js     (Currently express-mysql session - Configuration for JWT auth (JSON Web Tokens) optional)
index.js    (Entry point)
```

## Security Best Practice
https://expressjs.com/en/advanced/best-practice-security.html

## Credit
nodejs makati










## Sequelize Extra Setup
```
var sequelize = new Sequelize('database', 'username', 'password', {
  // custom host; default: localhost
  host: 'my.server.tld',

  // custom port; default: 3306
  port: 12345,

  // custom protocol
  // - default: 'tcp'
  // - added in: v1.5.0
  // - postgres only, useful for heroku
  protocol: null,

  // disable logging; default: console.log
  logging: false,

  // max concurrent database requests; default: 50
  maxConcurrentQueries: 100,

  // the sql dialect of the database
  // - default is 'mysql'
  // - currently supported: 'mysql', 'sqlite', 'postgres', 'mariadb'
  dialect: 'mysql',

  // you can also pass any dialect options to the underlying dialect library
  // - default is empty
  // - currently supported: 'mysql', 'mariadb'
  dialectOptions: {
    socketPath: '/Applications/MAMP/tmp/mysql/mysql.sock',
    supportBigNumbers: true,
    bigNumberStrings: true
  },

  // the storage engine for sqlite
  // - default ':memory:'
  storage: 'path/to/database.sqlite',

  // disable inserting undefined values as NULL
  // - default: false
  omitNull: true,

  // a flag for using a native library or not.
  // in the case of 'pg' -- set this to true will allow SSL support
  // - default: false
  native: true,

  // Specify options, which are used when sequelize.define is called.
  // The following example:
  //   define: {timestamps: false}
  // is basically the same as:
  //   sequelize.define(name, attributes, { timestamps: false })
  // so defining the timestamps for each model will be not necessary
  // Below you can see the possible keys for settings. All of them are explained on this page
  define: {
    underscored: false
    freezeTableName: false,
    syncOnAssociation: true,
    charset: 'utf8',
    collate: 'utf8_general_ci',
    classMethods: {method1: function() {}},
    instanceMethods: {method2: function() {}},
    timestamps: true
  },

  // similiar for sync: you can define this to always force sync for models
  sync: { force: true },

  // sync after each association (see below). If set to false, you need to sync manually after setting all associations. Default: true
  syncOnAssociation: true,

  // use pooling in order to reduce db connection overload and to increase speed
  // currently only for mysql and postgresql (since v1.5.0)
  pool: { maxConnections: 5, maxIdleTime: 30},

  // language is used to determine how to translate words into singular or plural form based on the [lingo project](https://github.com/visionmedia/lingo)
  // options are: en [default], es
  language: 'en'
})
```
