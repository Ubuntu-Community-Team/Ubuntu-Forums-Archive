---
title: "Removing XP"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Snitz on 2008-03-31
Hello,

Since I installed Ubuntu, I'm not login in into XP anymore and I'm pretty much comfortable with Ubuntu.
Is it secure to remove any trace of windows xp at this moment?

And if yes, how can I remove the windows partition and merge it with the Ubuntu filesystem?

---

### Post by nebu on 2008-03-31
Download gparted live cd then make a disc and boot from it --- [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)


start gparted


delete your NTFS partition


resize you main ubuntu partition or make another partition withe the space which was given to ur windows partition

---

### Post by kpkeerthi on 2008-03-31
Use gparted available in [system rescue cd]("http://www.sysresccd.org/"). You should be able to delete the XP partition and resize your ubuntu partition. 

1. Right-click XP partition and choose delete. This will produce some unallocated space.
2. Now right-click ubuntu partition and choose resize. Drag and allow it to fill all of unallocated space you created in step 1.
3. Click Apply

For more info see [gparted documentation]("http://gparted.sourceforge.net/documentation.php")

Once you get this far, let us know. We'll help you remove Windows XP entry from the GRUB too. :)

EDIT: I recommend system rescue cd. It doubles as a killer 'rescue' system for linux.

---

### Post by luceerose on 2008-03-31
The removal of XP should be pretty safe.
(Would someone else just like to verify there's no ramifications to removing ntldr from mbr ?)

As far as merging partitions etc, I recommend the "Gnome Partition Manager live disc". Just google it to find the .iso, then burn it to a disc.

EDIT: nebu & kpkeerthi beat me to it. I type too slow.

---

### Post by prismpirate on 2008-03-31
Or if you don't have GPart, just use the live cd, go the 

System > Administration > Partition Editor 

and format the NTFS or FAT partition into ext3.

---

### Post by farueulogy on 2008-03-31
All sounds pretty scary to me - I'd just do a fresh install of ubuntu but I'm a noob/beginner.

I know gparted is a good tool. I use it to deal with my exterior hard drive.

---

