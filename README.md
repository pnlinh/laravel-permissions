
# Laravel Permissions for Vue.js

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/76f6b99f5836453aa24720f03078f536)](https://www.codacy.com/app/williamcruzme/laravel-permissions?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=williamcruzme/laravel-permissions&amp;utm_campaign=Badge_Grade)
[![npm](https://img.shields.io/npm/v/laravel-permissions.svg)](https://www.npmjs.com/package/laravel-permissions)
[![npm](https://img.shields.io/npm/l/laravel-permissions.svg)](LICENSE)

<br>

laravel-permissions is a plugin for [Vue.js 2](https://vuejs.org/) that allows you to use [Laravel Permissions](https://github.com/spatie/laravel-permission) in your components.

Being blade-based you only need to specify the directive in your components or DOM elements. The names of the directives are the same as those available in [Laravel Permissions](https://github.com/spatie/laravel-permission#using-blade-directives), and EXTRA MORE!.

## Installation

#### yarn

```
yarn add laravel-permissions
```

#### npm

```
npm i laravel-permissions --save
```

#### CDN

laravel-permissions is also available on these CDNs:

- [jsdelivr](https://cdn.jsdelivr.net/npm/laravel-permissions@latest/dist/laravel-permissions.min.js)
- [unpkg](https://unpkg.com/laravel-permissions)

> When using a CDN via script tag, all the exported modules on LaravelPermissions are available on the LaravelPermissions Object.

## Getting Started

In your script entry point:
```javascript
import Vue from 'vue';
import LaravelPermissions from 'laravel-permissions';

Vue.use(LaravelPermissions);
```

Now you are all setup to use the plugin.

## Usage

Apply the custom directive on your components or DOM elements. Make sure to [read the example](examples).

### Directives

#### Permissions

Check for a specific permission:

```vue
<button v-permission="'add articles'">Add Article</button>

<!-- Alias -->
<button v-can="'add articles'">Add Article</button>
```

Check for any permission in a list:

```vue
<button v-permission:any="'add articles|edit articles'">Configure</button>
```

Check for all permissions:

```vue
<button v-permission:all="'add articles|edit articles'">Configure</button>
```

Check for unless permission:

```vue
<p v-permission:unless="'add article'">You dont have permission!</p>
```

#### Roles

Check for a specific role:

```vue
<button v-role="'writer'">Add Article</button>
```

Check for any role in a list:

```vue
<button v-role:any="'writer|admin'">Add Article</button>
```

Check for all roles:

```vue
<button v-role:all="'writer|user'">Add Article</button>
```

Check for unless role:

```vue
<p v-role:unless="'super'">You are not an Super Admin!</p>
```

#### Working with attributes

 You can also set True to any attribute of DOM element if the condition is not met. You can set multiple attributes.

```vue
<button v-permission:has.disabled="'add articles'">Add Article</button>

<input v-role:any.required.autofocus="'admin|super admin'" />
```

### Methods

#### Set permissions and roles

This plugin searches the Laravel instance, by default it already creates it but you must define the permissions and roles:

```js
this.$laravel.setPermissions(['add articles', 'edit articles']);
this.$laravel.setRoles(['admin', 'user', 'writer']);

this.$laravel.getPermissions(); // ['add articles', 'edit articles']
this.$laravel.getRoles(); // ['admin', 'user', 'writer']
```

#### Directives as functions

You can also use the custom directives as functions.

```js
this.$laravel.hasPermission('add articles'); // True
this.$laravel.unlessPermission('add articles'); // False
this.$laravel.hasAnyPermission('add articles|edit articles'); // True
this.$laravel.hasAllPermissions('add articles|edit articles'); // True

this.$laravel.hasRole('admin'); // True
this.$laravel.unlessRole('admin'); // False
this.$laravel.hasAnyRole('admin|writer'); // True
this.$laravel.hasAllRoles('admin|writer'); // True
```

## Examples

See the [examples and instructions](examples) with Laravel.

## Contributing

You are welcome to contribute to this project, but before you do, please make sure you read the [contribution guide](CONTRIBUTING.md).

## Credits

- Inspired by Laravel's [permissions syntax](https://github.com/spatie/laravel-permission#using-blade-directives).

## License

MIT
