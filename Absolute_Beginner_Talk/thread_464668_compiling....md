---
title: "compiling..."
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by nonoykevin on 2007-06-04
my ubuntu doesnt have a c or c++ compiler...how and where can i get this compiler?
because when i compiled my .cpp or .c program it searches for stdio.h or iostrem...
thanks

---

### Post by divague on 2007-06-04
in a terminal put

$sudo apt-get install g++

---

### Post by WW on 2007-06-04
Actually, to get the minimal set of packages to compile C and C++ programs, you can install the package **build-essential**.  You can use Synaptic, or the command
```

$ sudo apt-get install build-essential

```

---

### Post by Dougie187 on 2007-06-04
For c the compiler (in the build-essential package) is called gcc.

---

