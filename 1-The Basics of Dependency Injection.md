Chapter 1-The Basics of Dependency Injection
==============================

***Dependency Injection* is a set of software design principles and patterns that enables you to develop loosely coupled code**.

```C#
// original version
public class ClassA
{
    public void DoWork() 
    {
        var b = new ClassB();
        b.DoStuff();
    }
}
 
public class ClassB
{
    public void DoStuff()
    {
        // Imagine implementation
    }
}

// new version
public class ClassA
{
    private readonly ClassB _dependency;
 
    public ClassA(ClassB classB) => _dependency = classB;
 
    public void DoWork() => _dependency.DoStuff();
}
 
public class ClassB : IThing
{
    public void DoStuff()
    {
        // Imagine implementation
    }
}
```
Firstly, we no longer use the new keyword to instantiate an instance of ClassB. Instead, we have specified the type it depends on within the constructor. An instance of ClassB must be provided when that constructor is called. This applies a form of **Inversion of Control (IoC)** since ClassA is no longer in control of creating an instance of ClassB.

We can apply a further principle to this code:
```C#
public interface IThing
{
    public void DoStuff();
}
 
public class ClassA
{
    private readonly IThing _dependency;
 
    public ClassA(IThing thing) => _dependency = thing;
 
    public void DoWork() => _dependency.DoStuff();
}
 
public class ClassB : IThing
{
    public void DoStuff()
    {
        // Imagine implementation
    }
}
```
We have now applied the dependency inversion principle from SOLID. We no longer depend on a concrete implementation. Instead, we depend upon the IThing abstraction.

<!-- <div class="alert alert-info p-1" role="alert">
    
</div> -->

<!-- ![alt text](./zImages/17-6.png "Title") -->

<!-- <code>&lt;T&gt;</code> -->

<!-- <div class="alert alert-info pt-2 pb-0" role="alert">
    <ul class="pl-1">
      <li></li>
      <li></li>
    </ul>  
</div> -->

<!-- <ul>
  <li><b></b></li>
  <li><b></b></li>
  <li><b></b></li>
  <li><b></b></li>
</ul>  -->

<!-- <span style="color:red">hurt</span> -->

<style type="text/css">
.markdown-body {
  max-width: 1800px;
  margin-left: auto;
  margin-right: auto;
}
</style>

<link rel="stylesheet" href="./zCSS/bootstrap.min.css">
<script src="./zCSS/jquery-3.3.1.slim.min.js"></script>
<script src="./zCSS/popper.min.js"></script>
<script src="./zCSS/bootstrap.min.js"></script>