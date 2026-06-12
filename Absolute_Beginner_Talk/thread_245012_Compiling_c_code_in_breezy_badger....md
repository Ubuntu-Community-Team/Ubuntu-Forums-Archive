---
title: "Compiling c code in breezy badger..."
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2006-08-27
If I wish to compile a c program in ubuntu how do I do it? I have only ever worked with java in windows before, where I would save a .txt file as a .java file then compile it. 

So in Ubuntu how would I do this?

Thanks
Andrew

---

### Post by Mr Egg on 2006-08-27
Install GCC from in Synaptic and then write your code and save it as whatever.cpp then goto terminal (Applications > Accessories > Terminal) and write

```

g++ whatever.cpp -o whatever
```

This will compile your code into the executable name whatever. I hope that helps.

---

