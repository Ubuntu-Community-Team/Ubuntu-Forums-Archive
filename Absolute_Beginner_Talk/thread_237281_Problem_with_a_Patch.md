---
title: "Problem with a Patch"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by jgeeting on 2006-08-15
I am trying to get my Verizon Wireles Card (KPC650) working correctly, I knew from research it might be a challenge. Good news is it works sort of... 
I need to patch the Kernel with the one from this page [http://www.junxion.com/opensource/linux_highspeed_usbserial.html](http://www.junxion.com/opensource/linux_highspeed_usbserial.html)
in order to use the maxSize parameter and by all the how to-s I have read this will fix my problem. 
I run the patch -p0 < patchfile command and get this error in the terminal...

joe@ubuntu-laptop:~$ patch -p0 </home/joe/Desktop/patchfile
can't find file to patch at input line 6
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|
|# diff -Naur usb-serial.c usb-serial-v620.c
|
|--- usb-serial.c        2005-03-01 23:38:37.000000000 -0800
|+++ usb-serial-v620.c   2005-07-22 10:09:59.000000000 -0700
--------------------------
File to patch:

I am very new and want to learn, but I don't know what to try next.

---

### Post by siacs on 2006-08-17
You might want to try posting in [Wireless Support]("http://ubuntuforums.org/forumdisplay.php?f=139") next. You're probably more likely to get a response on this over there.

---

### Post by PriceChild on 2006-08-17
You need to completely compile a new kernel for yourself and patch the files in there with this patch.

Check out [http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)
For details on how to compile the latest kernel.

---

