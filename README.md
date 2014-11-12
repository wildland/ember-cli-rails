# ember-cli-rails

A rails template and build script for working with [ember-cli](https://github.com/stefanpenner/ember-cli)
and deploying with a rails api / backend. The goal is to allow ember-cli to be 
in charge of building and testing your ember app, and rails to be in charge of 
building and testing your rails app.


## Dependencies

You will need the usual dev setup ruby, rails, bundler, node && npm. Once you
have those, you will also need `bower` and `ember-cli`

install `bower` via npm

```bash
$ npm install -g bower
```

install `ember-cli` via npm

```bash
$ npm install -g ember-cli
```

## Usage

```bash
$ rails new <app-name> -m https://raw.githubusercontent.com/inigo-llc/ember-cli-rails/master/template.rb
```

You now have a rails project with an ember-cli project within it.

The template will set a catch-all rails route that serves up the ember app.
**You'll need to update your ember app config to set `location: 'hash'` manually
for this to work.** As you add api endpoints to rails be sure to place them
before the catch all route.

## Daily development

To work on the project, cd into the project root and:

```bash
$ bin/rails s
```

In another tab cd into your ember app (it'll be inside the rails root and 
labled with your app-name-ember). From within the ember-app directory run the
development ember server

```bash
$ npm start
```

This will proxy api calls to your rails backend. For more information see the 
[ember-cli docs](http://iamstef.net/ember-cli/)


## Deployment

From time to time, or whenever time to deploy, cd to your rails root and run:

```bash
$ rake ember:build
```

This will utilize `ember-cli` to build your ember app, and copy files over to 
your rails `public/` directory.
