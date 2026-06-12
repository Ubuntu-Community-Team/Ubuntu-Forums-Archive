---
title: "command line installs"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by soho2014 on 2007-05-09
I have tried the ./configure   make and   make install   commands in ubuntu, always with failure.

I thought that Ijust go to the directory of the unpacked program and issue these commands but somehow it never works.  Is there something different about ubuntu that causes this?

I thought that maybe it was because I couldn't log in as root  - some sort of restriction in ubuntu.  I would just feel better when i thought that I had mastered the install process for any sort of program that I encounter ,but thus far ,I"ve always failed in the command line method, except sometimes I've had success with sudo apt-get install programname.

Does anyone know anything about this?:guitar:

---

### Post by aysiu on 2007-05-09
Any reason in particular you're compiling from source instead of installing through the repositories? What's the program you're trying to install?

---

### Post by Iarwain ben-adar on 2007-05-09
Do you get any reproducable errors? That would be nice :D

Also, when installing from source, read what the error tells you.
Almost every time it wil tell you library_xyz has'nt been found, so you need to apt-get that ;)


Iarwain

---

### Post by soho2014 on 2007-05-09
usually it would say:

bash: ./ configure command not found.  or file not found, or something like that.

---

### Post by Iarwain ben-adar on 2007-05-09
It's
```
./configure
```
not 
```
./ configure
```

Don't add a space between the / and 'configure' ;)


Iarwain

---

### Post by qpieus on 2007-05-09
sounds like you need to install the build-essential package```
sudo apt-get install build-essential
```

you need this package in order to be able to build from source.

---

### Post by soho2014 on 2007-05-09
OK, thank you posters.

I wondered if there was a space or not between ./ and configure.  I learn now that there is not, and also that I need the build essential to be done. 

This will probably solve my problems.  I will try this when I get home!

---

