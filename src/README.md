<!--

WARNING!! DON'T EDIT THE FILE README.md on the root of the project, that one is a GENERATED FILE!

You should just edit the source file at src/README.md - the one which stars with ## @@title

-->

## @@title

<img src="img/angularjs.png" />

@@author @ [Avenue Code](http://www.avenuecode.com)

*@@email*

@@date

---

## Agenda

 - Overview
 - Controllers
 - Services
 - Directives
 - Routes
 - Hands-on
 - Conclusion
 - Challenge

----

## Prerequisites

- Intermediate Javascript
- Design Patterns

---

## Overview

- Created by Google, maintained by community
- MVW (Model View Whatever) architecture
- Lets you extend HTML vocabulary
- JS and HTML codes on where they belong
- Dependency Injection
- 2-way data-binding

----

## 2-way data-binding


Bad | Good
--- | ----
<img src="img/oneway.png" /> | <img src="img/twoway.png" />

----

## Don't think jQuery

> AngularJS should be thought in a declarative way of programming

 - No DOM manipulation
 - No jQuery. There's *always* an AngularJS way of write it
 - Data-binding into templates

---

 ## Basics

  - ng-app
   - Designates root element (e.g html, body)
  - ng-model
  - {{ }}

```html
<html ng-app>
[...]
<input type="text" ng-model="yourName" placeholder="Enter a name here">
<hr>
<h1>Hello {{ yourName }}!</h1>
<p>{{ 1 + 1 }}</p>
<pre>{{ data.result | json }}</pre>
[...]
</html>
```

----

## Controllers

<img src="img/controller.png" />

----

## Controllers

```html
<div ng-controller="MagicCtrl">
  <button ng-click="doTheMagic" />
  <span ng-show="magicText"> Including {{ magicText }}</span>
  <ul ng-repeat="text in texts">
    <li>{{ text }}</li>
  </ul>
</div>
```

```javascript
function MagicCtrl($scope) {
  $scope.texts = [
    'Abra',
    'Kadabra'
  ];

  $scope.doTheMagic = function() {
    var text = 'Alakazan';
    $scope.magicText = text;
    $scope.texts.push(text);
  };
};
```

---

## Services

 - Singleton classes/functions
 - Contain business logic
 - Fetch & manipulate data
 - Serve Controllers, Directives, Filters, etc

<img src="img/service.png" />

----

## Services

```javascript
angular.module('myModule').service('MagicService', function() {
  var magicTexts = [
    'Abra',
    'Kadabra',
    'Alakazan'
  ];
  this.getMagicText = function() {
    return magicTexts.pop();
  };
});
```

```javascript
function MagicCtrl($scope, MagicService) {
  $scope.texts = [];

  $scope.doTheMagic = function() {
    var text = MagicService.getMagicText();

    $scope.magicText = text;
    $scope.texts.push(text);
  };
};
```

----

## Services

> AngularJS services are REST-friendly :)

```javascript
angular.module('mod', ['ngResource']).factory('Magic', function($resource){
  return $resource('path/to/magic/');
  // You can also set some params on path or headers
  // Alternatively you can use $http.get('path/to', successHandler)
});
```
```javascript
function MagicCtrl($scope, MagicService) {
  $scope.texts = [];

  $scope.doTheMagic = function() {
    MagicService.get().then(function(data) {
      $scope.magicText = data;
      $scope.texts.push(data);
    });
  };
};
```

---

## Directives

> Markers on a DOM element that tell AngularJS to attach some behavior on it
or its children.

 - Can have its own controller or HTML template
 - 3 levels of usage: element, attribute or CSS class

----

## Directives

```html
<ul ng-repeat="user in users">
  [...]
</ul>
```

```html
<p ng-hide="hideMe">[...]</p>
```

```html
<ng-view>
 [...]
</ng-view>
```

- Other examples:
  - ng-model
  - ng-href
  - ng-src
  - ng-class

---

## Routes

- Deep-linking URL to controllers and views
- Give a better experience on SPA (Single-Page Application)
- Full manipulation (reload, intercept, history) on application

```javascript
angular.module('todoList', []).config(function($routeProvider) {
  $routeProvider.when('/', {
    templateUrl : 'views/main.html',
    controller : 'MainCtrl'
  }).when('/todo', {
    templateUrl : 'views/todo.html',
    controller : 'TodoCtrl'
  }).otherwise({
    redirectTo : '/'
  });
});

```

---

## Hands-on

- Basic To-Do application
- Scaffolding an AngularJS app on Yeoman

---

## Conclusion

- Full client-side MVW framework
- A "new" declarative way of working with Javascript
- Provides a large toolset to build simple and complex applications
- Great community contributing on its extension and maintenance

---

## Reference & Guidance

- http://docs.angularjs.org/guide
- http://angular-ui.github.io/
  - http://angular-ui.github.io/bootstrap/
- http://www.cheatography.com/proloser/cheat-sheets/angularjs/
- http://directivemaker.info/#!/
- Stack Overflow & Github :)

---

## Challenge

- You will create an AngularJS application to check current weather on a given city name
- Use following API
  - http://api.openweathermap.org/data/2.5/weather?q=Belo%20Horizonte
- Let your imagination flies and use directives to create CSS/image changes
- Extra points for those who add Geolocation to the API ;)

*Submit the code on your Github account*

---

# Thank you!

Questions?
