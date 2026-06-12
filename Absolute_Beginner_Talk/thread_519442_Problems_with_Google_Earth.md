---
title: "Problems with Google Earth"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by William S on 2007-08-07
Hi
I got a little problem with Google Earth. When I click on desktop icon nothing happens, and then I try terminal and get this message:```
  /googleearth-bin: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory
 
```

Any suggestions here?

---

### Post by aquavitae on 2007-08-07
Looks like a broken package.  Check for broken packages in synaptic (its in one of the menus) and see if that helps.  Otherwise try installing libxcursor1.

---

### Post by William S on 2007-08-07
Solved the start problem with the broken package by downloading some 32 bit modules. Now the splash screen pops up at least, and then it freezes.    I got ATI video card, and I searched the forums and other places that drivers for ATI sucks for Ubuntu. 
Can this have anything with the problem?

---

### Post by xopher_mc on 2007-08-07
Type this into terminal

[HTML]glxinfo | grep rendering[/HTML]

if the answer is no 

then follow this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) :)

---

