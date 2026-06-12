---
title: "Refit recognizing linux hard drive as &quot;legacy os&quot;."
date: 2008-01-13
forum: Apple Intel Users
---

### Post by macaholic on 2008-01-13
So I have 2 hard drives in this computer, a 250 GB for osx, windows and a failsafe linux, and then another one just for my main linux. Now I installed rEFIt through OSX, and when I used to just have 1 hard drive, OSX, Windows, Linux, it say all three of them just fine. Now when ever I boot up, it recognizes the 3 on the one hard drive, and the other linux as a "Legacy Os", and I have to boot up and select it through GRUB again, something I do not have to do with the linux partition on the other hard drive. This makes boot time much longer, and any help would be appreciated.

---

### Post by benanzo on 2008-01-13
I believe that refit will only recognize three boot volumes, in your case Windows, Mac and the first Linux.  This is a limitation of the GUID partitioning scheme used by Mac OS X.  Really your only option is to boot the fourth system via grub after selecting the first linux system (the one that appears on the refit menu.)  If you want to be really tricky about it you can install all four to an MBR disk then use grub to boot everything instead of having to use refit.  The only problem is that Mac OS X will refuse to install to an MBR disk, so you need to install it normally as it wants to be, then tar up the new OS X install and move it to whichever MBR disk partition you want.  Grub is more than happy to boot OS X, you don't technically need the GUID.

---

