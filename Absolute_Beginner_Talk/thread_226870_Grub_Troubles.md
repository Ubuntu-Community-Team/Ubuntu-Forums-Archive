---
title: "Grub Troubles"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by greenbean on 2006-07-31
1.) Downloaded the ISO file for the desktop version from this site.

2.) Created the bootable CD

3.) Ran the install on a brand new Maxtor ATA/133 hard drive 300GB (the only drive on the machine) and I let the installer use all of it's defaluts for the formatting of the hard drive.

4.) Install ran very smoothly and then it asked me to restart the machine and remove the CD; which I did.

5.) When the machine reboots it stops with an error code of 18 looking for GRUB.

I know GRUB is a boot manager but I don't know why the install put it on the drive when this is the only OS on the machine or how to get around the problem unless this is a part of the "default" install process I need to circumvent.  I'm hoping there's a way to fix this because what little I've seen of Ubuntu has really peaked my interest.  I've only used Windows for last 10 years and know just about nothing of Linux et al.

---

### Post by confused57 on 2006-07-31
You might try reinstalling grub:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by greenbean on 2006-08-07
Thanks,  I found the cause to be other greenbean problems.  I found the checksum was bad on the CD and then my BIOS was apparently set up incorrectly for memory voltages causing hundreds of memory errors which windows xp seemed to just shrug off and keep on running but the kicker was probably that my hard drive size being reported to BIOS was 33.8G when it should be 300.1G and even though LINUX seemed to see the 300G just fine I still reset the drive reporting software back to 300G.  At least now I'm back to my original problem the Ubuntu 6.06 which is the system locks up completely from time to time and I have to restart the machine.  Even if I just leave it sitting doing nothing it'll lock.  Time to start a new thread...

---

