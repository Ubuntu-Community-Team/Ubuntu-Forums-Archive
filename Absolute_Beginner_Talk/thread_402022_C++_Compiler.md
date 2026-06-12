---
title: "C++ Compiler"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-05
I made a source file (.CPP) and I cannot seem to open it with a compiler :O, I am new to programming, I installed the Intel compiler that they are giving away for free, as well as the Eclipse compiler, yet I cannot seem to compile the source code, anyone have tips?

---

### Post by LaRoza on 2007-04-05
Check out the  Programming Forum.

Even though compiling has been addressed before, here is the simple answer:

open the terminal:

1. cd to the directory with your source file

2. TYPE "g++ yourfile.cpp -o executablesname"
   don't type the quotes.

3. Run the program from the terminal.

---

### Post by jvc26 on 2007-04-05
You may also need to install the package build-essential:
```

sudo apt-get install build-essential

```
Il

---

### Post by Peter1234123 on 2007-04-05
Is it possible to compile apps for Windows with G++?

---

### Post by LaRoza on 2007-04-05
Compile? No, but you can recompile the source with another compiler. For a free compiler, try Dev-C++ by Bloodshed at  

[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

You can also get the same compiler as a portable app, that is, you can run it off a flash drive at any windows computer.

---

