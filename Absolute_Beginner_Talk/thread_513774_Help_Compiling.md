---
title: "Help Compiling"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by danthebugman on 2007-07-30
So I'm pretty new to Linux and I've been trying to compile a program called SCID.  It's the only program I can't live without from my Windows days and yes it is available through the repositories, but it's an older version of the program that hasn't been updated.  The version that I have the source for is a newer one being continued by another programmer.  There is no .deb package so it's gotta be compiled from source.  Not a huge deal to me, I'm enjoying the new challenges Linux is offering (I say challenges in a good way).  Anyway after unzipping the source code and running "./configure" in the command line this is what I get:

configure: Makefile configuration program for Scid
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.4
    Your operating system is: Linux 2.6.20-16-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.4 library: /usr/lib
    Location of Tk 8.4 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.

So judging that the location of tcl.h and tk.h could not be found the settings in the Makefile were wrong and need to be changed, but I do not know what they should be.  Could someone more experienced than myself enlighten me??

Regards,
Daniel :confused:

---

### Post by tbroderick on 2007-07-30
Do you have tk8.4-dev and tcl8.4-dev installed?

---

### Post by danthebugman on 2007-07-30
Turns out they weren't.  Thanks I'll try it again.

Regards,
Daniel :)

---

### Post by danthebugman on 2007-07-30
Ok so everything went as it is supposed to...I guess...I can't seem to find how to run the program now.  Is there a way I can add it to the menu bar, like under "Games" or something??

Regards,
Daniel :confused:

---

### Post by phidia on 2007-07-30
In the terminal do "whereis scid" you should be able to find the executable from that list.
It would probablly be placed in /usr/local/bin but that could be different depending on the make install parameters.
You can right click on either panel and choose "Add to Panel..." you will want the "Custom Application Launcher" selection.

---

