---
title: "someone please explain this"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by casperzshado on 2007-06-01
why cant you run en exe file on ubuntu?

---

### Post by Stephen Howard on 2007-06-01
.exe tends to be appended to a file compiled using run-time libraries from ms-windows or ms-dos operating systems

Ubuntu is an graphical interface for the linux operating system.

You might as well ask microsoft why they can't run a program compiled for linux.

That said, you might be able to run the a .exe file using the *wine libraries* - they are designed to be binary compatible with microsoft run-time libraries.

---

### Post by casperzshado on 2007-06-01
how do i install my software for me audio and video cards?

---

### Post by casperzshado on 2007-06-01
and aslo what are the wine libraries?

---

### Post by bapoumba on 2007-06-02
Thread moved to "Absolute Beginner Talk".

---

### Post by Lord Illidan on 2007-06-02
> **casperzshado said:**
> how do i install my software for me audio and video cards?

Tell us what your audio cards and video cards are first.

From [www.winehq.org](www.winehq.org) :

> Wine is an Open Source implementation of the [Windows]("http://www.microsoft.com/windows/") API on top of [X]("http://www.x.org/"), [OpenGL]("http://www.opengl.org/"), and  Unix.
  Think of Wine as a compatibility layer for running Windows programs.  Wine does not require Microsoft Windows, as it is a completely free alternative  implementation of the Windows API consisting of 100% non-Microsoft code,  however Wine can optionally use native Windows DLLs if they are available. Wine  provides both a development toolkit for porting Windows source code to Unix  as well as a program loader, allowing many unmodified Windows programs  to run on x86-based Unixes, including [Linux]("http://www.linux.org/"), [FreeBSD]("http://www.freebsd.org/"), [Mac OS X]("http://www.apple.com/macosx/"), and [Solaris]("http://wwws.sun.com/software/solaris/").


---

### Post by justifier on 2007-06-02
you are best trying to find linux versios of the software, what is the exact name of the software you are using? and what are your graphics sound cards? make,model etc 

Wine is a experimental process adn WILL NOT ALWAYS WORK for all windows programs. To install wine type in terminal.

sudo apt-get install wine

---

### Post by Lord Illidan on 2007-06-02
> **justifier said:**
> you are best trying to find linux versios of the software, what is the exact name of the software you are using? and what are your graphics sound cards? make,model etc 

Wine is a experimental process adn WILL NOT ALWAYS WORK for all windows programs. To install wine type in terminal.

sudo apt-get install wine

That is correct. Also, don't try and install drivers from wine. Wine is commonly used to play some games, like starcraft, world of warcraft, etc.

---

### Post by drowner on 2007-06-02
You are having trouble with your video drivers?

Or are you just assuming you will need to install them?

---

