---
title: "installing the new ATI driver (v 8.34.8)"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by raynard79 on 2007-06-22
Hi all, 

I recently got the new linux ATI drivers (version 8.34.8) from a linux magazine, and am having trouble installing it..

It came with a:
 
               "ati-driver-installer-8.34.8-x86.x86_64.run"  	

file, which I saved on my desktop.

I then went into a terminal and went as root, and typed:

               "root@nug:/home/raynard/Desktop# sh ati-driver-installer-8.34.8-x86.x86_64.run"

It seemed like it was all working, but then it stopped with the following error:
[INDENT]
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.34.8..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Unknown X Window

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install[/INDENT]

So I put in:

   " X_VERSION=x710_64a ./ati-driver-installer-<ver>-<arch>.run [--install]"

and then i get:

   " -su: ver: No such file or directory"

Any suggestions?

I think ver is the fglrx-install directory....no?

And should I create this manually? And if so where? (/etc/...)

any help would be much appreciated..

Thx.

R.

---

### Post by Pconfig on 2007-06-22
You might want to replace <ver> and <arch> with the real version and architecture stuff.

---

### Post by Enverex on 2007-06-22
.... new? That driver is 3 or 4 months old and has been superseeded 3 times since.

Download the new driver (8.37.x) and run "sh whatever.run --buildpkg Ubuntu/feisty" (assuming you're using Feisty).

---

### Post by raynard79 on 2007-06-23
hahah... i am still new to this.. 

i will get the newer ones, thanks for your help/ advice. Let you know how it goes.

Cheers, 
R

---

### Post by raynard79 on 2007-06-23
ps. how do i find out which architecture it is?

pps. is the version the version of the driver, or the version of the xorg.server?

---

### Post by dragnazz5.0 on 2007-06-24
im trying to do the same thing and it wont let me.  i could be typing it wrong but who knows.

---

### Post by fumduck on 2007-06-24
this thread had a solution to Ati driver
[http://ubuntuforums.org/showthread.php?t=464150]("http://ubuntuforums.org/showthread.php?t=464150")
Good luck

---

