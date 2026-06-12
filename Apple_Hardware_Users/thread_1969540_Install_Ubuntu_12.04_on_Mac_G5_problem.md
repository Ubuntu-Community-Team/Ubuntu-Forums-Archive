---
title: "Install Ubuntu 12.04 on Mac G5 problem"
date: 2012-04-30
forum: Apple Hardware Users
---

### Post by johannes2510 on 2012-04-30
Situation:
Mac G5 dual 2,3 GHz; 2 drives; 
one drive with 2 partitions (Tiger 10.4.11/Data); can't touch; work drive.
second drive with 3 partitions (Leopard 10.5/Data/Empty for install Ubuntu created with iPartition)

Downloaded, burned and booted on live cd without problems.

Problem: when I have to choice where install Ubuntu (12.04 for PPC of course) the installer show the correct partition on first drive (with Tiger) but on the second drive he show me only "empty space". Don't see the 3 partitions but only one "device"...  All partitions on both drives are Mac OSX extended journaled.
I have try to disconnect the first drive (with Tiger) but no change.
Anyone know why this happen? Where I am wrong?
Thanks in advance for help.

---

### Post by rsavage on 2012-04-30
Hi Johannes, I've had in the past a similar problem where the installer/gparted can't see partitions.  Can you see them in disk utility?  In my case I just assumed I'd mucked up the partition map somehow (it was after a lot of messing about).  It worked after I reformated the drive - probably something you don't want to do?

---

### Post by johannes2510 on 2012-04-30
> **rsavage said:**
> Can you see them in disk utility?

Yes

> **rsavage said:**
> It worked after I reformated the drive - probably something you don't want to do?

Exact...

The strange thing is that in one drive gparted see the partitions and in the other no... 

Thanks for sharing your experience.

---

### Post by johannes2510 on 2012-05-01
Ok, I have formatted and do a clean install. The G5 boot and ubuntu run well.
After that with live cd I have created again the old partitions and all is well.
But No sound...
I am searching solutions.
Any ideas?
Thanks

---

### Post by rsavage on 2012-05-01
Sound: [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)
 
You have to delete the file /etc/modprobe.d/blacklist.local.conf .

---

### Post by johannes2510 on 2012-05-01
> **rsavage said:**
> 
 
You have to delete the file /etc/modprobe.d/blacklist.local.conf .

That works!
Thankyou.
Now I have sound from internal speaker.
Still search for my Motu 828 mk2 firewire audio interface...

---

