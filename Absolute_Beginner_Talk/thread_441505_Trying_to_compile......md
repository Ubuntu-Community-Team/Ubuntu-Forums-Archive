---
title: "Trying to compile....."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by johnnyphive on 2007-05-12
...and here is what I get as output.  Can somebody help me out?

$ gcc -o unsc04 ecma-267.c unscrambler.cunscrambler.c:22:19: error: stdio.h: No such file or directory
unscrambler.c:23:20: error: string.h: No such file or directory
unscrambler.c:24:18: error: time.h: No such file or directory
unscrambler.c: In function ‘add_seed’:
unscrambler.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
unscrambler.c:51: error: ‘NULL’ undeclared (first use in this function)
unscrambler.c:51: error: (Each undeclared identifier is reported only once
unscrambler.c:51: error: for each function it appears in.)
unscrambler.c: In function ‘test_seed’:
unscrambler.c:70: warning: incompatible implicit declaration of built-in function ‘memcpy’
unscrambler.c: In function ‘unscramble_frame’:
unscrambler.c:97: warning: incompatible implicit declaration of built-in function ‘memcpy’
unscrambler.c:101: warning: incompatible implicit declaration of built-in function ‘printf’
unscrambler.c: In function ‘main’:
unscrambler.c:113: error: ‘FILE’ undeclared (first use in this function)
unscrambler.c:113: error: ‘in’ undeclared (first use in this function)
unscrambler.c:113: error: ‘out’ undeclared (first use in this function)
unscrambler.c:115: error: ‘time_t’ undeclared (first use in this function)
unscrambler.c:115: error: expected ‘;’ before ‘start’
unscrambler.c:120: warning: incompatible implicit declaration of built-in function ‘printf’
unscrambler.c:130: warning: incompatible implicit declaration of built-in function ‘fprintf’
unscrambler.c:130: error: ‘stderr’ undeclared (first use in this function)
unscrambler.c:135: warning: incompatible implicit declaration of built-in function ‘fprintf’
unscrambler.c:149: error: ‘start’ undeclared (first use in this function)
unscrambler.c:167: error: ‘NULL’ undeclared (first use in this function)
unscrambler.c:168: warning: incompatible implicit declaration of built-in function ‘fprintf’
unscrambler.c:175: warning: incompatible implicit declaration of built-in function ‘fprintf’
unscrambler.c:187: warning: incompatible implicit declaration of built-in function ‘fwrite’

---

### Post by Happy_Man on 2007-05-12
And have you installed build essential?

```
sudo apt-get install build-essential
```

---

### Post by johnnyphive on 2007-05-12
Doing that now, I'll let you know.

---

### Post by johnnyphive on 2007-05-12
Now i'm getting something different

$ gcc -o unsc04 ecma-267.c unscrambler.cunscrambler.c: In function ‘main’:
unscrambler.c:128: warning: assignment makes pointer from integer without a cast
unscrambler.c:133: warning: assignment makes pointer from integer without a cast

in creates "something" but when i try to run it i get

$ unsc04
bash: unsc04: command not found


What now?

---

### Post by Happy_Man on 2007-05-12
The basic steps to compiling are:

For a .tar.gz named lala that extracts into a folder lala-files and is for the program fairy, the steps to compiling it would be like so:
Extract the .tar.gz. Then open a terminal and type this ONE LINE AT A TIME:
```
cd /home/happy/lala-files
make
sudo make install

```

What are you compiling, anyway?

---

### Post by johnnyphive on 2007-05-12
nevermind, got it figured out.  I was trying to run unsc04 when what i needed to be typing was ./unsc04

what is with the ./

---

### Post by FuturePast on 2007-05-12
When running a command the shell (terminal) checks the PATH environment variable to find the command.
By default the current directory is not in PATH.
./ means look in the current directory.

---

### Post by johnnyphive on 2007-05-12
10-4

Learn something new everyday

Thanks!

---

