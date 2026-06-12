---
title: "[SOLVED] Installing GCC"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2008-01-14
For my Computer Programming I class we will be using the GCC compiler. So, I have decided to install it on my Ubuntu distro (Gutsy). However, I am still not very proficient at installing .tar files. I have already downloaded the package and extracted it to the desktop using the tar xfvz command, but now I do not know how to take the file and actually install it to the file system. I read the documentation how to on installing files not included in the add/remove software manager but it tells me to read the readme in the file but the readme is not any help so far. How do I install this? And when it gets installed how do I run the actual compiler? Thanks :)

---

### Post by thisismalhotra on 2008-01-14
Hey dude,

you need not install the files from website. Use "Synaptic" package manager in ubuntu ... serch for gcc and select to install ... here this will help.. it has direction for .tar.gz too but you dont need it for gcc..

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Good luck !! Buzz us if u have any issues ...

---

### Post by Tenken on 2008-01-14
There is no need to install the gcc from a .tar. You can install build-essentials (which includes gcc) through Synaptic, or from the command line with this

```
sudo apt-get install build-essential
```

the compiler has a nice man page, but if you don't want to read it:

```
cd /where/my/program/is
gcc -o program.whatever program.cpp
```

---

### Post by Joeb454 on 2008-01-14
Please note that while the above post is indeed correct, it will most likely ask for the install CD to be inserted.

also the syntax for gcc which I use (for C code, not C++ code) is this:

```
gcc myprogam.c -o myprogram.bin
```

---

### Post by skaldicpoet9 on 2008-01-14
Right on, thanks guys :)

---

### Post by stchman on 2008-01-14
> **skaldicpoet9 said:**
> For my Computer Programming I class we will be using the GCC compiler. So, I have decided to install it on my Ubuntu distro (Gutsy). However, I am still not very proficient at installing .tar files. I have already downloaded the package and extracted it to the desktop using the tar xfvz command, but now I do not know how to take the file and actually install it to the file system. I read the documentation how to on installing files not included in the add/remove software manager but it tells me to read the readme in the file but the readme is not any help so far. How do I install this? And when it gets installed how do I run the actual compiler? Thanks :)

gcc is installed by default on all Ubuntu installations.  I also believe that build-essential is installed by default on Gutsy as well.

If not then type the following in a terminal:

```

sudo apt-get -y install build-essential
```

Ubuntu comes with many programming languages install d by default.

---

### Post by pieisgood4589 on 2008-01-14
Like python! :)

---

### Post by Joeb454 on 2008-01-14
Thanks for marking the thread solved :)

---

### Post by Majorix on 2008-01-14
> **Joeb454 said:**
> Please note that while the above post is indeed correct, it will most likely ask for the install CD to be inserted.

If you disable CD under Software Sources or Synaptic you will not be asked for the CD ever again.

---

### Post by skaldicpoet9 on 2008-01-14
One more question actually...how do I use the editor? Is there a different program I need to use?

---

