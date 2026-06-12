---
title: "Python.h - Unable to find, install etc."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by edoules on 2007-03-14
Dear all,

I'm new to Ubuntu, Linux and Python.

For a class assignment, I have to develop a python script which calls C functions-- I therefore need to install python with Python.h...

Thus far, installing python from synaptic, the terminal etc. has yielded nothing. Searching the file system manually in the src, includes, bin etc. locations as well as with the search command yields nothing.

I can't set gcc to the include folder because it doesn't exist.

Notes:
- using Python 2.4.4 (Must be this version, not 2.5.x)
- tried to install python, python-dev.

Any assistance appreciated.

Thanks,
Ed

---

### Post by chewearn on 2007-03-16
Not sure if this will help; before I can compile C programs (using gcc), I need to install build-essential

```
sudo aptitude install build-essential
```

---

### Post by stevieP on 2008-02-04
After running into the same problem, i.e. getting the same error message during a build of pdb2pqr, and doing some google searches, I found a solution by using synaptic to install python2.4-dev , which contains header files and a static library for Python.

-sP

---

