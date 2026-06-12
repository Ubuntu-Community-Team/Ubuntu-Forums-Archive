---
title: "what is a development libary ?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Capra on 2006-08-25
what is a development libary ?

---

### Post by az on 2006-08-25
The file you load into memory is executable code (a binary).  It was not written in binary or executable code but in source form.  Then it was compiled into the executable format.

If you want to add stuff on to an application, you can go about it two ways:
1- you can add your code to the original source and then recompile everything
2- you can just work on the bits you need and stick it together.  To do this, you usually only need the headers for the compiled bits.  The headers are used to make your new code interact properly with the precompiled bits.

A -dev package is the headers for the precompiled library.

I hope that is what you were asking.

---

