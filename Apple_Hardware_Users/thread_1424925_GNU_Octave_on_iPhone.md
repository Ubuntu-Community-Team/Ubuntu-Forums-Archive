---
title: "GNU Octave on iPhone"
date: 2010-03-08
forum: Apple Hardware Users
---

### Post by carlosgs91 on 2010-03-08
.

---

### Post by carlosgs91 on 2010-03-08
.

---

### Post by nixscripter on 2010-03-08
Not an iPod expert, but it looks like you're missing headers for glibc ("stdio.h not found"). Either that, or your path is not set correctly.

---

### Post by carlosgs91 on 2010-03-08
.

---

### Post by linuxopjemac on 2010-03-08
```
sudo apt-get install build-essential
sudo apt-get install automake
```

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by carlosgs91 on 2010-03-08
.

---

### Post by linuxopjemac on 2010-03-09
These programs you need to compile software. See the link I gave you.

---

### Post by Atilana on 2010-03-10
Hi, i had the same issues before, thanks for the comments are very useful

---

### Post by nixscripter on 2010-03-12
> **linuxopjemac said:**
> These programs you need to compile software. See the link I gave you.
But that is for native compiling. He needs to cross compile, assuming that he is compiling on the PC.

I have always found building cross toolchains (compiler, linker, etc.) a pain. I always used [Getntoo crossdev]("http://en.gentoo-wiki.com/wiki/Crossdev") for that.

However. I can say that there should be native libraries (i.e. those for the iPod) and their headers. You will need to set variables on the configure script invocation to indicate where they are. How much stuff did you build/download for the cross toolchain?

If I am mistaken and you are trying to compile on the iPod itself... good luck.

---

### Post by carlosgs91 on 2010-03-13
.

---

### Post by a5k3r on 2010-09-16
Just a suggestion.

You can compile GNU Octave for ARM architecture on your PC using arm-linux-gcc and then transfer the binary to your iPod. 

I haven't tried it on iPod and GNU Octave. But I used to do that for a robot that I was working on.

---

### Post by macacos on 2011-10-26
Another simple way to use Gnu Octave on your iPhone::popcorn:
[http://itunes.apple.com/de/app/octave-remote/id467653632?mt=8](http://itunes.apple.com/de/app/octave-remote/id467653632?mt=8)

For me it works!!!

---

### Post by cococo on 2012-10-18
hi, i just install on my iphone the app Octave Remote but doesn't work.
I insert the commands like:

a = 1

and select to calculate.

the app return:

connection to server failed.

Can you help me?

---

