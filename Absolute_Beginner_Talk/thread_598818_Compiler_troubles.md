---
title: "Compiler troubles"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-10-31
Hi there, i'm having some trouble getting gcc to work.
I'm making a very basic program using c and c++ in gedit, and attempting to compile, but upon trying to compile i get the following error:
jordan@jordan-laptop:~/Work$ g++ -Wall -O test test.cpp
test: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o:(.text+0x0): first defined here
test:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
test: In function `_fini':
/build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crti.S:41: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crti.o:/build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crti.S:41: first defined here
test:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
test: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.1.3/crtbegin.o:(.data+0x0): first defined here
test: In function `_init':
/build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/crti.o:/build/buildd/glibc-2.6.1/build-tree/i386-libc/csu/crti.S:15: first defined here
/tmp/ccWg8Bhv.o: In function `main':
test.cpp:(.text+0x6a): multiple definition of `main'
test:(.text+0xf6): first defined here
/usr/bin/ld: warning: Cannot create .eh_frame_hdr section, --eh-frame-hdr ignored.
/usr/bin/ld: error in test(.eh_frame); no .eh_frame_hdr table will be created.
collect2: ld returned 1 exit status

i'm not sure if this is saying that my compiler is installed incorrectly, or if it doesnt recognize something that gedit is doing.  Anyone know what my problem here might be? it's not a coding error,

---

### Post by jordank on 2007-10-31
crap. sorry bout the emoticons.

---

### Post by jordank on 2007-10-31
it's compiling the program into an exe file. is this maybe the reason nothing happens when i try to run it? linux doesnt support exe's does it?

---

### Post by taurus on 2007-10-31
Have you installed the build-essential package before you compiled your program?

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by jordank on 2007-10-31
Hey there, i tried the sudo aptitude commands, but that didnt change anything.  
However, i noticed something odd.
when i type the command
g++ -Wall -o test test.cpp
i get no errors, and appears to compile correctly, but the .exe file, when i try to run it, does nothing.
but when i type
g++ -Wall -O test test.cpp
i get that screen full of errors.  Does the capital O do something completely different?
even if it did, it seems as if:
a) my compiler is faulty
or 
b) linux doesn't like .exe files.

any ideas?

---

### Post by jordank on 2007-11-01
does linux work with .exe files?

---

### Post by Adramelech on 2007-11-02
Linux does not run exe files, wine can add a layer to run exes.

Exe files are for windows, ELF files are the ones that run on linux, not PE, if you want to compile exe files you need to do some crosscompilation, is not hard to set, use mingw.

try:
gcc test.cpp

TEST IS A LINUX COMMAND IF YOU RUN "test" YOU ARE GOING TO RUN A LINUX COMMAND NOT YOUR NEW COMPILED PROGRAM, CHANGE THE NAME, OR RUN IT AS "./test"

---

### Post by ozylog on 2007-11-02
try this:
sudo apt-get install build-essential

---

### Post by Celegorm on 2007-11-02
> **jordank said:**
> when i type the command
g++ -Wall -o test test.cpp
i get no errors, and appears to compile correctly, but the .exe file, when i try to run it, does nothing.
but when i type
g++ -Wall -O test test.cpp
i get that screen full of errors.  Does the capital O do something completely different?

'-o test' tells the compiler to call the executable 'test' while '-O' tells the compiler to optimize the code. In linux, the extension on a filename doesn't necessarily have anything to do with the file type. Whether or not a file is executable is part of a files permissions.

---

### Post by mali2297 on 2007-11-02
> **jordank said:**
> 
g++ -Wall -o test test.cpp
i get no errors, and appears to compile correctly, but the .exe file, when i try to run it, does nothing.

The compiler should then have created an executable file with the name **test** (without extension). Try to run it with the command
```

./test

```

---

### Post by jordank on 2007-11-02
> **mali2297 said:**
> The compiler should then have created an executable file with the name **test** (without extension). Try to run it with the command
```

./test

```

Awesome, thank you very much, this worked.
Would you mind explaining to me WHY it needs to be run as ./test?
Thanks :)

---

### Post by Celegorm on 2007-11-02
This is because the current directory is not included in the $PATH environment variable. When you type a command name, bash looks for an executable to run in all of the directories listed in $PATH. The "./" at the beginning of "./test" tells it to only look for test in the current directory.

---

### Post by jordank on 2007-11-02
thank you sir.

---

### Post by Can+~ on 2007-11-02
Summary:

[LIST=1]
[*]Linux is case sensitive. Using "cpp -o" is different than "cpp -O"
[*]Linux doesn't care about extensions. Although you should use them.
[*].exe files built for windows, won't run on linux, except for wine or any other emulator.
[*]To run a file use ./<nameOfYourFile>
[*]build-essential is needed to compile C and C++.
[*]To run a file you need permission to do so. You can use either "sudo ./<name>" (not recommended), or change it's permissions/owner using "chown" "chgrp", etc.
[/LIST]

---

