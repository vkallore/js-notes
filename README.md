# js-notes

- [js-notes](#js-notes)
  - [React.js life cycle](#reactjs-life-cycle)
    - [Mounting](#mounting)
    - [Updating](#updating)
    - [Unmounting](#unmounting)
    - [Error Handling](#error-handling)
  - [React.js Performance](#reactjs-performance)
  - [React.js Functional programming libraries](#reactjs-functional-programming-libraries)
  - [map, filter & reduce](#map-filter--reduce)
    - [map](#map)
    - [Advantages](#advantages)
    - [filter](#filter)
    - [reduce](#reduce)
  - [Progressive Web App - PWA](#progressive-web-app---pwa)
  - [ServiceWorker](#serviceworker)
    - [ServiceWorker Advantages](#serviceworker-advantages)
    - [ServiceWorker Lifecycle](#serviceworker-lifecycle)
    - [ServiceWorker Scope](#serviceworker-scope)
  - [JS Scope](#js-scope)
  - [Client Side Storage](#client-side-storage)
  - [Closure](#closure)
  - [Event Loop](#event-loop)
  - [Execution Context](#execution-context)
  - [Variables](#variables)
    - [Primitive](#primitive)
    - [Reference Types](#reference-types)
  - [Prototype chain](#prototype-chain)
  - [useEffect](#useeffect)
  - [strict mode](#strict-mode)
  - [Design Patterns](#design-patterns)
    - [What is it?](#what-is-it)
    - [Benefits](#benefits)

## React.js life cycle

### Mounting

- constructor()
- static getDiversedStateFromProps()
- render()
- componentDidMount()

### Updating

- static getDiversedStateFromProps()
- shouldComponentUpdate()
- render()
- getSnapshotBeforeUpdate()
- componentDidUpdate()

### Unmounting

- componentWillUnmount()

### Error Handling

- componentDidCatch()

## React.js Performance

1. Minify JS, try out CDN if using script tag if not caching the static resource must be at higher level (leverage browser cache)
2. Use production build
3. Uglify-js using browserify/brunch/rollup
4. Bundle the work
5. Long data lists - use "windowing" using "react-window" or "react-virtualized"
6. Avoid unwanted re-rendering (conciliation) (shouldComponentUpdate or extend the class with React.PureComponent), this doesn't help always, but to a certain level it can!
7. Debounce Input Handlers

## React.js Functional programming libraries

1. Ramda
   a. CURRYING - Allows to create a fn from another fn, by not providing all args.
   b. Mutate safe
2. Loadash (built from \_)
3. Underscore (oldest)

## map, filter & reduce

### map

Already have an array, want to do same operation & return same amount of items.

### Advantages

1. No need to manage the state of loop
2. No need to use the index of loop
3. No need to create a new array and push values always. It returns (return is a must) complete new array.

### filter

Already have an array, want to have items in it, which matches some criteria. Must return boolean.

### reduce

Already have an array, want to use values in it, and create completely new.

## Progressive Web App - PWA

These apps loads instantly regardless of network state & puts up its own UI on the screen without requiring a network round trip (even when its offline)

## ServiceWorker

It is a background worker, which acts as a programmable proxy, allowing us to control what happens on a request by request basis. We can make it to work React apps to work offline.

### ServiceWorker Advantages

1. Push API - sending push notifications even when the webapp is not running.
2. Background Sync: for deferring actions until the user has stable connectivity. This is handy for making use whatever the user wants to send is actually sent.

### ServiceWorker Lifecycle

1. Registration - in script. It informs the browser where service worker is located
2. Installation - it registered with navigator.serviceWorker.register('file-path.js'), which returns a promise on success. & scope can also define as second arg.
3. Activation -

### ServiceWorker Scope

It defines from which path it will intercept requests.

## JS Scope

The set of identifies that each env has access to is known as scope. We cab next these scopes into hierarchical chain of envs, known as the "scope chain"

## Client Side Storage

1. Session storage
2. Cookies
3. IndexedDB
4. WebSQL
5. Local Storage.

## Closure

Closures are functions that refer to independent (free) variables. In other words, the function defined in the closure remembers the environment in which it was created.
**_use case_**: maintain private ref to a var in the outer scope

## Event Loop

FIFO

## Execution Context

Execution context is an abstract concept used by the ECMAScript specification totrack the runtime evaluation of code. This can be the global context in which your code is first executed or when the flow of execution enters a function body

At any point in time, there can only be one execution context running. That’s why JavaScript is “single threaded,” meaning only one command can be processed at a time. Typically, browsers maintain this execution context using a “stack.” A stack is a Last In First Out (LIFO) data structure, meaning the last thing that you pushed onto the stack is the first thing that gets popped off it. (This is because we can only insert or delete elements at the top of the stack.)

## Variables

### Primitive

A primitive is data that is not an object and has no methods.

1. Boolean
2. Null
3. Undefined
4. Number
5. String
6. Symbol (in ES6) (unique and immutable primitive value and may be used as key of an Object value)

### Reference Types

1. Object

## Prototype chain

This is a `finite` chain of objects which is used to implement `inheritance`and `share properties`.

## useEffect

Combined version of _componentDidMount_,
_componentDidUpdate_ & _componentWillUnmount_

## strict mode

1. Cannot use a variable undeclared.
2. Can have strict mode applied inside the function too.
3. Cannot delete a variable or function.
4. Cannot duplicate parameter name of a function.`function (v1, v1){}`.
5. Octal numeric literals are not allowed. Eg: `var v1 = 010`.
6. Octal escape sequences are not allowed. Eg: `var v1 = "\010"`.
7. Writing to a read only property is not allowed. `"use strict"; Object.defineProperty(obj, " x", {value: 0, writable: false}); obj.x = 2;`
8. Writing to a get only property is not allowed. `"use strict"; var obj = {get x() {return 0}}; obj.x = 2;`
9. Deleting an undeletable property is not allowed. `delete Object.prototype;`
10. The words `eval`, `arguments` cannot be used as a variable.
11. The `with` statement is not allowed. `with (Math){x = cos(90)};`
12. For security reasons, `eval()` is not allowed to create variables in the scope from which it was called. `eval("var x = 2"); console.log(x)`
13. The `this` keyword in functions behaves differently. It refers to the object that called the function. If the object is not specified, functions in strict mode will return `undefined` and functions in normal mode will return the global object. Eg: `function myFunction() { console.log(this); this.name = 'FLIP'; console.log(this); } myFunction();`
    // How to make the above code working?
    `var myFn = new myFunction();`
14. Future proof: keywords reserved for future JS versions cannot be used as variable names in strict mode. These are
    - implements
    - interface
    - let
    - package
    - private
    - protected
    - public
    - static
    - yield

## Design Patterns

### What is it?

A pattern is a reusable solution that can be applied to commonly occurring problems in software design.

### Benefits

- Patterns are proven solutions.
- Patterns can be easily reused.
- Patterns can be expressive.
