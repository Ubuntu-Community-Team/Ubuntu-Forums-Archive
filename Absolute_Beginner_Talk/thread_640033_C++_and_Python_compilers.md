---
title: "C++ and Python compilers?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-13
I was just scanning through the package manager and saw some things with python or cpp in their names. Does this mean that Ubuntu came with editors/compilers for these languages? I do some C++ writing for school and use CodeBlocks compiler. Does Ubuntu come with something like that? If so, how do I find/use it?

Also, unrelated; which is better Gnumetric spreadsheet editor or Openoffice spreadsheet editor? I only want one because I hate redundant programs.

---

### Post by chippy99 on 2007-12-13
From a terminal type "sudo aptitude install build-essential". This will install the GCC compiler and other tools.

Have never used Gnumetric but the open-office spreadsheet works fine for me.

---

### Post by stchman on 2007-12-14
> **EmosSuck777 said:**
> I was just scanning through the package manager and saw some things with python or cpp in their names. Does this mean that Ubuntu came with editors/compilers for these languages? I do some C++ writing for school and use CodeBlocks compiler. Does Ubuntu come with something like that? If so, how do I find/use it?

Also, unrelated; which is better Gnumetric spreadsheet editor or Openoffice spreadsheet editor? I only want one because I hate redundant programs.

Python and gcc/g++ are installed by default.  You will need to install build essential to use the compilers though.

---

### Post by Origin415 on 2007-12-14
gcc comes installed, but it is just a compiler, you dont use it to actually write the programs.

For that you would need something like Eclipse.

```
sudo aptitude install eclipse eclipse-cdt
```

---

