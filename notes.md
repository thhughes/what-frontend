# Learning 
Sometimes I learn things, sometimes I punish myself. Who knows what this is. 


# Class 1 
## Definitions worth remembering 
* React is a view only library. It's the view in MVC arch UI pattern 
* ES6 is the standard name for Javascript. It's version 6 of the ECMA Script programming language. 
* JSX -> Javescript Syntax Extension. Can use HTML/XML in Javascript. 

## Syntax
* Define a variable with: 
    * `var` -> lazy evaluation scope of the variable 
    * `let` -> scope is limited to a block of code 
    * `const` -> read only variable definition
    * Take the following example. If you were to change the definition of <???> in different ways different things would happen. `var` would compile correctly and work. `let` will error when the final console log is found because `i` is out of scope. `const` will error because `i` is read only and cannot be modified on the first `i++`.
        ```javascript
        function foo(){
            for (<???> i=0; i<5 ; i++){
                console.log(i);
            }
            console.log(i);
        }
        ```
        
* Block -> scoped area
* `console.log(...)` -> `print`/`printf`
* operators 
    * All standard except `,` operator. It evaluates a list of things and returns the furthest right option. e.g.: 
        *  `a = (a++, a)` is just `a++`. But `a = (a++, 100)`, `a` will always be `100`
    * `==` vs. `===`: 
        * `==` will perform a typless check. One of them will get cast to the other and they'll compare value. 
        * `===` compares types before doing a value check. 
    * `typeof` Returns the type of the given operand
    * `delete` Deletes an object, object’s attribute or an instance in an array
    * `void` Specifies that an expression does not return anything
* Expression Keywords: 
    * `this` points to the current object
    * `super` calls methods on an object’s parent, for example, calk parent’s constructor
    * `function` used to define a function
    * `function*` used to define a generator function
    * `async` function: used to define an async function

### Loops
Iterating over for loops: 

Simple: 
```
for (let i of [0, 1, 2]) {
    console.log(vals[i]);
}
```

More Exact: 
```
for (let i = 0; i < other; i++) { 
    /// Blah
}
```

### Functions
General pattern: 
```
function sum(a, b) { 
    console.log("Hello world") 
    const res = a + b
    console.log(" The Sum of " + a + " + " + b + "is: " + res)
    return res  
}
```

Functions as variables - aka anonymous functions.
```
var functionVarName = function()
{
  console.log("Hello! I'm an Anonymous function");
}

myFunction();
```


#### Function Generator Methods 
Need examples 

#### Arrow Function 
Function definition is: 
```
var var_name = (Arg1, Arg2..) => { // Do something };
```
It's supposed to be a more compact function definition and has all kinds of shortcuts. All these are the same: 
```
function getGreetingFunc() {
  return 'Welcome to JavaScript';
}

// JavaScript ES6 arrow function with body
const getGreetingArrow1 = () => {
  return 'Welcome to JavaScript';
}

// JavaScript ES6 arrow function without body and implicit return
const getGreetingArrow2 = () =>
  'Welcome to JavaScript';
```

We can see why this is valuable in the following example: 
```
const students = [
  { ID: 1, present: true},
  { ID: 2, present: true},
  { ID: 3, present: false}, 
];

const presentStudents = students.filter(function(student){return student.present;});
// OR
const presentStudents = students.filter(student => student.present);
console.log(presentStudents);
```
The simplification comes from these rules: 
* If there is only one statement inside function body then you can omit return keyword as well the curly braces
* Omit the function keyword in the beginning
* You can also get rid of parameter parentheses if you only have one parameter

### Array Methods to remember 
* `push` (append) 
* `upshift` (prepend) 
* `pop` (pop from tail) 
* `shift` (pop from head)
* `splice` add/remove from index 
Others are searchable 

### Object Destructing 
```
const student = {
  ID: '21',
  name: 'Jhon',
  GPA: '3.0',
};

const {ID, name, GPA} = student;
const {name:n} = student;  /// Get just the Name and use var N to encapsulate it 
```

Using destructuring in a function. Given a class type `props` that has a `greetings` member variable... 
```
/// You can access it normally
function Greeting(props) {
  return <h1>{props.greeting}</h1>;
}

/// Or Desaturate as you go
function Greeting({ greeting }) {
  return <h1>{greeting}</h1>;
}
```

### Spread Operator 
This breaks the contents out of the array into standard data. Much like `**kwargs` would pass the kwargs in python, this does similar. e.g.: 
```
a = [1,2,3];
b = [4,5,6];
c = a.concat(b)         /// One way to do this 
c = [...a, ...b];       /// Using the Spread Operator
console.log("c: " + c);
```

The real power of this though is how it can be used to merge data: 
```
const person = { name: "Jhon"};
const student = { ID: "21", GPA: "3.0"};

const new_object = { ...person, ...student, semester: '3'};
console.log(new_object);
```