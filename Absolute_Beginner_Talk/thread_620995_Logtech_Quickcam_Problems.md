---
title: "Logtech Quickcam Problems"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by canadiandude007 on 2007-11-23
Hello,

I have an old Logitech Quickam (with dark focus ring) that I'm trying to get to work on the latest Ubuntu version.

When doing an "lsusb" I found that the ID for the cam is 046d:d001 which coincides with a driver for DIVIO NW801/NW802.  Reference here: [http://www.qbik.ch/usb/devices/showdev.php?id=307](http://www.qbik.ch/usb/devices/showdev.php?id=307)

I tried following the instructions by first downloading the cvs and patch software.  Since the kernel is 2.6.22.14 I figured the following would work:

cvs -d:pserver:anonymous@nw802.cvs.sourceforge.net:/cvsroot/nw802 login
cvs -z3 -d:pserver:anonymous@nw802.cvs.sourceforge.net:/cvsroot/nw802 co -P nw802-2.4
cd nw802-2.4
cp Makefile.26 Makefile
patch -p0 < patch-2.6
make clean
make

The first line doesn't work whatsoever as it asks for a password, but I am able to grab the files and go into the nw802-2.4 folder, replace the Makefile and patch it.

When I run "make" there are problems with it finding the usbvideo.h and usbvideo.c files.  I've tried finding them on the Internet, copying the data into a text file and saving the information into the appropriate directories.

However I'm still having problems and not sure if it's due to the Makefile or what.

Is there an "apt-get install" command I can run to grab the linux source so that the usbvideo.c file is included in it (or for that matter, all files are included)?

Any other thoughts of what to try?  Errors I've received have been during the compilation of the files that they are referencing non-existent files.

Help please.

Thanks!

---

### Post by bratliff on 2007-11-23
Let me know if you solve the problem. My quickcam pro 4000 does not work on any im's.

Bratliff

---

### Post by RobotoWorks on 2007-11-23
My Quickcam has almost the same problem, its only about a month old, so Im hoping that its not too new that Ubuntu wont support it. Any help would be much appreciated. I installed Camorama and Ekiga but nothing worked. But when I type in lsusb in terminal it does recognise the web cam.

---

### Post by canadiandude007 on 2007-11-28
See updates to this thread: [http://ubuntuforums.org/showthread.php?t=621240](http://ubuntuforums.org/showthread.php?t=621240)

---

### Post by philinux on 2007-11-28
[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)

you could try this driver.

---

