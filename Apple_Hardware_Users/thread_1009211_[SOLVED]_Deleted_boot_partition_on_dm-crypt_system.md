---
title: "[SOLVED] Deleted /boot partition on dm-crypt system"
date: 2008-12-12
forum: Apple Hardware Users
---

### Post by MaddMatt on 2008-12-12
Hi all, 

So I deleted my /boot partition. It wasn't exactly an accident, but I didn't think it would be as difficult to restore as it currently is; Pre-deletion I used gparted to 'copy' the partition onto a USB key, but for whatever reason I am having great difficulty 'copying' it back. I think it's the combination of having a full-disk encrypted system with dm-crypt, and the EFI bootloader. I'm using rEFIt. 

So far I have tried copying the partition back to /dev/sda3, which I was not able to do (paste function was disabled), so then I re-created the partition, (ext3), gave it boot flags and did a cp -r -p of the files to the directory, which didn't work. 

I have also used the alternate cd to reinstall grub, which also is giving me a 'no system disk' message at boot. Good thing I have this OS X partition hanging around... 

Can someone please point out what I am doing wrong? Thank you!
M

---

### Post by MaddMatt on 2008-12-13
[BUMP]

Tried a couple of different things - figured out that gparted only copies one direction: AKA I can see the 'paste' option if I am copying from the hard disk to the USB key, not the other way. (why?) Really not happy about this... It's been 3 days since I have been able to log in. Lame. 

M

---

### Post by MaddMatt on 2008-12-14
Fine. I figured it out - it was a rEFIt issue, not a dm-crypt issue - copying the boot partition works, I just needed to let rEFIt update the MBR. 
M

---

### Post by cyberdork33 on 2008-12-15
> **MaddMatt said:**
> Fine. I figured it out - it was a rEFIt issue, not a dm-crypt issue - copying the boot partition works, I just needed to let rEFIt update the MBR. 
M
Just a clarification, that is not a rEFIt issue, that is a partition table issue. rEFIt just has the tools to fix the problem.

---

### Post by MaddMatt on 2009-01-08
Thanks for the clarification - say, what do you know about accidentally 'blessing' the sda2 (hd0,1) partition with grub? That is to say - I accidentally installed grub on the wrong partition - the OS X hfs+ partition. It never actually put a /boot directory on it, but I am assuming it did something to the MBR, because it is now listed in REFIT (and I used the tools again to update the MBR) but I can't seem to figure out how to get rid of it. Its an annoyance more than anything, but I would appreciate it if you had any insight into it. 
Cheers!
M

---

### Post by cyberdork33 on 2009-01-08
> **MaddMatt said:**
> Thanks for the clarification - say, what do you know about accidentally 'blessing' the sda2 (hd0,1) partition with grub? That is to say - I accidentally installed grub on the wrong partition - the OS X hfs+ partition. It never actually put a /boot directory on it, but I am assuming it did something to the MBR, because it is now listed in REFIT (and I used the tools again to update the MBR) but I can't seem to figure out how to get rid of it. Its an annoyance more than anything, but I would appreciate it if you had any insight into it. 
Cheers!
M
grub can't "bless" Unfortunately, it is not simple to remove the boot code from a partition.

---

