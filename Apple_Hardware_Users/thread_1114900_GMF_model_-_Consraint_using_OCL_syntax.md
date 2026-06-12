---
title: "GMF model - Consraint using OCL syntax"
date: 2009-04-03
forum: Apple Hardware Users
---

### Post by Hod Gil on 2009-04-03
Hello All

I am building a new model in GMF environment.
I have 2 kinds of features: Compoenent & Connection.
I want to add an additional constraint using OCL in order to make sure that an instance of a diagram will not contain component that is not attached to any link.
Something like:
For each (Component)
         Exist (Connection.SOURCE = Component) OR
         Exist (Connection.TARGET = Component)
I tried to use the Audit Container in the GMFMAP file,
and added an Audit rule, But I am really not familiar with the OCL Syntax and cannot do it right...
Can somebody help me with the syntax here???
Thanks & HAve a nice weekend!

---

### Post by cyberdork33 on 2009-04-03
I think you are in the wrong forum...

---

