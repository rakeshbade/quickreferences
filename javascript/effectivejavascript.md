# Effective JavaScript
68 SPECIFIC WAYS TO HARNESS THE POWER OF JAVASCRIPT

---

### Strict vs Non-Strict

**How can we concatenate these two files correctly?**
Concatenate files by wrapping their bodies in immediately invoked
function expressions. 
```javascript
// no strict-mode directive
(function () {
  // file1.js
  "use strict";
  function f() {
    // ...
  }
  // ...
})();
(function () {
  // file2.js
  // no strict-mode directive
  function f() {
    var arguments = [];
    // ...
  }
  // ...
})();
```
---

### Understanding JavaScript's Floating-Point Numbers
Even some of the simplest-looking arithmetic can produce inaccurate results
```javascript
0.1 + 0.2; // 0.30000000000000004
```
** For any real numbers x, y, and z, it’s always the case that (x + y) + z = x + (y + z).But this is not always true of floating-point numbers: ***
```javascript
(0.1 + 0.2) + 0.3; // 0.6000000000000001
0.1 + (0.2 + 0.3); // 0.6
```

##### Things to Remember:
* JavaScript numbers are double-precision floating-point numbers.
* Integers in JavaScript are just a subset of doubles rather than a
separate datatype.
* Bitwise operators treat numbers as if they were 32-bit signed integers.
* Be aware of limitations of precisions in floating-point arithmetic.

### NaN
First, JavaScript follows the IEEE floating-point standard’s headscratching requirement that NaN be treated as unequal to itself. So
testing whether a value is equal to NaN doesn’t work at all:
``` javascript
var x = NaN;
x === NaN; // false

isNaN(NaN); // true
//But other values that are definitely not NaN, yet are nevertheless coercible to NaN, are indistinguishable to isNaN:
isNaN("foo"); // true
isNaN(undefined); // true
isNaN({}); // true
isNaN({ valueOf: "foo" }); // true

var a = NaN;
a !== a; // true
var b = "foo";
b !== b; // false
```

### Primitives to Object Wrappers
```javascript
var s = new String("hello");
typeof "hello"; // "string"
typeof s; // "object"
```
Since each String object is a separate object, it is only ever equal to itself.
```javascript
var s1 = new String("hello");
var s2 = new String("hello");
s1 === s2; // false
```
**Observe without new**
```javascript
var s1 = String("hello");
var s2 = hello
s1 == s2 //true
typeof s1 //string
typeof s2 //string
```
### Operator ==
```javascript
undefined == null // true
undefined === null //false
```


