---
title: "Problems with dev/sda"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by schaefscha on 2007-08-06
Hi!
Lately I've been having a little trouble with mounting devices on the USB ports, after installing Feisty. Today has been the most painful one, since I can't even find where my dev/sdaX went to... now I can't mount my external hard drive.
I've done 
sudo fdisk -l  but the only things that came out were:

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4700    37752718+  83  Linux
/dev/hda2            4701        4864     1317330    5  Extended
/dev/hda5            4701        4864     1317298+  82  Linux swap / Solaris


Anyone has a clue were my dev/sdaX partitions went to? And how could I fix the problem and install my external hard drive?

Thanks a lot for your input and help!!!

---

### Post by Damanther on 2007-08-06
Seems like I remember feisty going away from the sd* naming but I could be thinking of another distro.  I think my external usb drive gets mounted as /dev/hde or something like that. I'll confirm when I get home, but you might check the output of dmesg and see if it is trying to give that device a name other than sd*

---

### Post by shriphani on 2007-08-06
Hello,
I faced the same issue a few months back. I had upgraded to a new kernel and the result was that my bus was recognised as IDE as opposed to the SCSI bus. I placed a bug report at launchpad.net and reverted back to the previous kernel till the problem got fixed. I had an ICH4 SATA controller that was the root cause of all problems. It is fixed now thankfully.

Regards,
Shriphani Palakodety

---

