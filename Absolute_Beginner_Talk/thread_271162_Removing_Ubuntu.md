---
title: "Removing Ubuntu"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by EvansLight on 2006-10-04
Well, not too long ago i got me a hand me down computer that i could use for whatever. So i decided it was time to learn Linux, and chose Ubuntu. But i installed both windows and ubuntu on this computer on the same hard drive.

I now have a new hard drive, and want to remove Ubuntu from this hard drive, and remove the boot loader thing, so its just windows. I was wondering how to do this. And i was also wondering if i can resize the windows partition to take up all of the first hard drive without hurting windows. Ive been using both for a while now, and have alot of imporant stuff, and hours of loading programs and such on the windows install. The ubuntu on the other hand has been totally messed up from my playing with it so i dont mind reinstalling it, and also getting to finnaly have it on its own harddrive :D

Any help would rock here!!

---

### Post by Crooksey on 2006-10-04
From windows, right click my computer, then device manager, then storage devices, the the hardrive management tool.

Delete from there all the Ubutnu aprtions, and if you want create new Widnows ones. Then reboot with your windows XP cd in the drive, from the CD get to the "recovery console" and type

fdsik /mbr

Then reboot removing the CD and you will boot straight into windows no bootloader and with 100% windows on the HDD.

---

### Post by Kateikyoushi on 2006-10-04
Ok I got it.

---

### Post by Crooksey on 2006-10-04
From the Hard-disk manager you can right click free space to make new partions.

---

### Post by EvansLight on 2006-10-04
yea see i was guessing i could just remove it through a partition manager. But i wanted to really know about if i could resize it. i remeber i was able to resize the windows partition after a fresh install to allow ubuntu to have room. So then i thought i could use the partition manager from the ubuntu cd to maybe resize it back.

Also how do i get into the recovery console?

---

### Post by Crooksey on 2006-10-04
Boot from your windows XP disk, and it will have onscreen options to get to the recovery console, most likely like press R or something. From the partion manager you cant add the free space to C: (i dont think), you would need to use a 3rd party partion program.

---

### Post by EvansLight on 2006-10-04
ok.... that sucked. I fully removed all Ubuntu partitions, then restarted my computer with the windows cd in the drive, and boom grubb gives an error, and the cd doesnt load. Then i try restarting, and it says 'No Operating System Found' XD i have hours into that windows install, i mean its not gonna kill me if i have to redo it, its gonna suck, but i can do it. Im trying to reisntall ubuntu right now, to see if for some reason that helps. oh this is sucking XD

EDIT: Yes for some reason its letting the Ubunutu CD load, but the windows one wont ](*,)

---

### Post by ajgreeny on 2006-10-04
After you have restored the windows MBR get a copy of the live CD version of gparted from
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Boot from it and you can then use it to delete the ubuntu partition from your original disk, making sure you leave the windows partition untouched.  You can also use it to enlarge the windows partition to the full disk size without any problem at all.  This is almost the same as I have done to my wife's machine, though on that I was simply deleting a fat32 partition and adding it to the windows partition, more than doubling the latter's size.  Works far better than any other partitioning software that I know of and is so simple to use.

---

### Post by Crooksey on 2006-10-04
Damaged WindowsCD?

---

### Post by jaboua on 2006-10-04
I belive qtparted and gparted can resize ntfs - they should be available on the (k)ubuntu CDs (run it live).

---

### Post by EvansLight on 2006-10-04
i checked twice it loads first on my laptop. as i said im right now reinstalling ubuntu, but with the minimal space it needs to install. 

IF this works then ill FIRST fix the boot then remove the ubuntu partition.

---

### Post by Thenotsowyzewun on 2006-10-04
Yes they are on the Ubuntu disc you have, and they can both resize ntfs safely (ntfstools haven't had a single report of this messing up according to their site).

---

