---
title: "Tape Drive Help"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Joey6 on 2007-01-18
Hello, guys!!

I am totally brand new to this forum and to Ubuntu.  I would like to migrate from WinXP to Linux, and the consensus is that Ubuntu is actually the best.  So far, I have been very pleased with the program.  I have tried Linspire, Knoppix, and I like this version better.

I have been able to install my wireless internet connection, have it recognized, and I have even written a "How-to" guide for other users of Linspire and Knoppix because WiFi, and all of its related hardware, is an issue that everyone has a problem understanding and getting it to work.  Much trial and error, and extreme frustration at times,,, but as you can see, I am on the internet with Ubuntu.

My problem is:  I need to have my tape drive recognized and I do not know where to start.  I am really not familiar with the Linux language but I follow instructions well.  The tape drive is:

Iomega Ditto Easy 3200 .  It is currently connected to the Floppy drive cable (as a slave?) through an in-line connector on this cable.  The floppy drive works fine.  Also, in "MY Computer", these are recognized as:  "Floppy" and another as "Floppy1".  The "Floppy" device is for the floppy drive, and, I assume, the "Floppy1" is for the tape drive. 

How do I configure the tape drive to work??  Please help!!

Joey.-](*,)

---

### Post by berto- on 2008-01-25
The first thing I'd check is to see if Linux is recognizing the drive.  You can do that by running "dmesg" from a terminal.  After rebooting, run the command:

```
dmesg | less -i
```

In the text that spits out you can search for text by hitting "/" then the text you're looking for, and then the <enter> key.  In this case, search for iomega:

```
/iomega<enter>
```

You can continue searching for more matches by hitting the "n" key.  When you're done, hit the "q" key and you'll get out of "less".

Hopefully, you'll see the tape drive in there.  If that's the case Linux sees your drive!  In the same area of text, see if you're informed of the "device" it's attached to, something along the lines of /dev/st0 or /dev/ft0.

Now that you know the device name, you are ready to use the drive.  The following site can help you actually using the drive.  This drive is connected through the floppy controller, so I think this documentation applies:

[http://www.linux.com/base/ldp/howto/Ftape-HOWTO.html#toc1](http://www.linux.com/base/ldp/howto/Ftape-HOWTO.html#toc1)

This page states your drive should be usable under Linux:

[http://www.linux.org/docs/ldp/howto/Ftape-HOWTO-6.html](http://www.linux.org/docs/ldp/howto/Ftape-HOWTO-6.html)

Good luck!
-Roberto.

---

