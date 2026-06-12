---
title: "[SOLVED] installing lyx- need xforms and xpm libraries"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by miao on 2007-11-01
Hello,
I'm trying to get LyX to work on my system. 
I recently upgraded to Feisty- so besides the automatic updates and build-essential, it can be assumed that I haven't installed just about anything. 

when I run ./configure, it eventually pops this out:

**** The following problems have been detected by configure.
**** Please check the messages below before running 'make'.
**** (see the section 'Problems' in the INSTALL file)

** Cannot find libXpm. Please check that the Xpm library
   is correctly installed on your system.

** Cannot find xpm.h. Please check that the Xpm library
   is correctly installed on your system.

** Cannot find libforms or libxforms. Please check that the xforms library
   is correctly installed on your system.

** Cannot find forms.h. Please check that the forms library
   is correctly installed on your system.

** Cannot find X window libraries and/or headers. Check your installation.
   If you use a Linux system, check that you have installed
   the development tools.

I've searched around but can't seem to find what I need. Any advice would be appreciated.
-Kat

---

### Post by llamakc on 2007-11-01
Is

```

sudo apt-get install lyx

```

broken?

---

### Post by miao on 2007-11-01
Wow am I ever stupid.

Disregard!

(PS-thanks)

---

