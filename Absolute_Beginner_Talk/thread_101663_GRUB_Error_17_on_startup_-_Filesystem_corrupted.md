---
title: "GRUB Error 17 on startup - Filesystem corrupted?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by tidemann on 2005-12-10
My Ubuntu 5.10 system has been running happily and stable for a while until I rebooted after some auto-upgrades. Instead of starting Ubuntu, I was faced with "GRUB Error 17" after BIOS. I am not dual-booting.

After a fair amount of cursing I got a Live-CD and booted successfully. I ran GParted and found several concerning errors (check screenshots). The partion of the hard-drive has an unknown filesystem, and casper-snapshot can not be read. I really want to get my old settings, files, ... etc back!

Please help!

---

### Post by tidemann on 2005-12-16
*bump* I'm looking for any possible solution...

---

### Post by hod139 on 2005-12-16
You can try [reinstalling grub]("http://ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub").  This won't alter any of your settings or files.

---

### Post by Mustard on 2005-12-16
If the above solution doesnt work....

I'm not too experienced with working with hard drive errors, but have you run fsck on the partitions?

They have to be unmounted to do so, so you would have to do it from a liveCD, which are using anway.

---

### Post by psusi on 2005-12-16
The casper stuff is the livecd not your hard drive, so ignore it. 

As for your drive... what exactly did you do to get it to this state?  It looks like it IS corrupted.  

You might try running sudo fsck -t ext3 /dev/hda1.

---

### Post by Emerzen on 2005-12-16
Hi,

I'm not sure why you're getting that error.  I would to a disk check from the LiveCD.  If that doesn't turn anything up, here's they simplest way to reinstall GRUB:

Insert INSTALL CD and reboot.  At 1st prompt type: rescue

Double check that the word "rescue" is at the top left corner of the screen after it boots.

It will ask you what file system to mount as root-> choose the disk and partition that contains Ubuntu (technically, that has your boot directory).

Once mounted type the following: grub-install /dev/hda (if your MBR is on your 1st drive--most likely.)  If MBR is on another drive replace hda w/ hdb, etc...  One more thing-> if you have a SATA drive, replace the h->s.  

Good luck!

---

