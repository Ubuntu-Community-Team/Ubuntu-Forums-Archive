---
title: "Can you clone your harddrive?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-14
Can you clone your harddrive like the way Norton Ghost does on Windows, exept doing it on Linux? I think I heard it was possible. If so, how do you do this?

---

### Post by DirtDart on 2006-07-14
Depends on the OS (Ubuntu I'm assuming!), the boot loaders, and your file system.

[Link](http://service1.symantec.com/SUPPORT/ghost.nsf/docid/1999021909463125?Open&src=&docid=2000033111503625&nsf=ghost.nsf&view=docid&dtype=&prod=&ver=&osv=&osv_lvl=) to Symantec's info on Ghost & Linux.

---

### Post by wieman01 on 2006-07-14
Try "Unison":

[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html")

I am using it to synchronize my laptop with my desktop computer. But it equally works with local hard-drives.

---

### Post by mcduck on 2006-07-14
Linux has 'dd' command that does exact clones..

If I remember right, 'dd /dev/hda1 /dev/hdb1' would clone first partition of hda to first partition of hdb. This does raw copy, so if you have 20GB partition with 5GB files, dd will copy 20GB. 

try 'man dd' for more info & correct syntax for the command.

edit: as dd does raw copying, it doesn't matter what filesystem is on the disk. for dd it's just 1's and 0's ;)

---

### Post by Sonofmoog on 2006-07-14
> **jincast90 said:**
> Can you clone your harddrive like the way Norton Ghost does on Windows, exept doing it on Linux? I think I heard it was possible. If so, how do you do this?

In addition to the other suggestions in this thread, you might want to check out PartImage, which is a Linux tool for backing up entire drives.

It would help to know what you're trying to accomplish.  If you want backup, you can use Windows applications like Ghost or Drive Image, as well as Partimage.  

If you're looking to copy a drive's contents from partition 1 to partition 2, then I'd suggest dd.  There's a sophisticated way of using tar to accomplish the same task, but I don't recommend it.

My own needs are for whole backups that I can restore when an install - either Windows or Linux - goes south, so I use Drive Image version 6, and I can verify that it works fine on Linux filesystems, both backup and restore.  The program no longer exists (its features have been folded into Ghost), but you can likely pick up a copy on eBay.

---

### Post by Frank Golden on 2006-07-14
What I have done is use partimage to make a recovery image
of my current install stored on an external USB HDD.
Then if the need arises I can use partimage to restore the image.
It is a byte by byte copy with all programs and data preserved.
The advantage of using partimage is that it only copies used space in the partition you are copying. For example if you have
a 20GB partition that has 4GB used that is all that will be copied. You can get partimage as a standalone program. Or
as part of the LinuxRescue CD.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
 
You download and burn a CD as instructed on the above site.

There is some info on that site about using partimage.

Aysiu at [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)
has info at this site but his info is for using the Live CD
to install partimage to memory and run. You may want to 
google for more info also.
Great tool. After you learn how to use it I think it's easier
than Ghost.

---

### Post by wthanna on 2006-07-14
What you are looking for is G4U (Ghost for Unix). I believe it is in the repositories. It is made to do exactly what you are asking. It works with many file systems, by the way, not just *nix.

---

### Post by Frank Golden on 2006-07-14
> **wthanna said:**
> What you are looking for is G4U (Ghost for Unix). I believe it is in the repositories. It is made to do exactly what you are asking. It works with many file systems, by the way, not just *nix.
Interesting [http://theatomicmoose.ca/g4u/](http://theatomicmoose.ca/g4u/) neat program. Think I'll still 
use partimage though. Reading info on site g4u copies all of partition including
unused space. For example if Ubuntu is 3Gb on a 10B partition you would
use 10GB of space to copy it. Partimage only copies used space. g4u
looks to be easier to learn or at least there appears to be easier to
understand instructions on their web site. However once you learn partimage
it is easy to use. I would be glad to help the Jincast90 with using partimage if
needed. 
    
   I presently have a standalone image of Ubuntu 6.06 and an image
of Ubuntu 6.06 from my dual boot drive stored on a USB HDD.
I have had to use both images recently because I am a chronic tinkerer.
Remember if it ain't broke, fix it 'til it is.:p Partimage gets you up and
running with a perfect, if earlier copy in about 20-30 minutes.
Sure beats re-install.

---

### Post by jincast90 on 2006-07-14
It sucks, that most programs wants you to clone the entire partition. I dont have space for that lol.

---

### Post by Drakkor on 2006-07-14
I know this sux,but I backed up my entire second hard drive,(Ubuntu) with Acronis True Image..........in windoze. You can set a compression level to be much lower than the the original. :mrgreen:

---

### Post by tabinin on 2006-07-14
After reading a few posts in the forums I was able to successfully clone my 80GB drive to a 160GB drive in two steps.  Here is what I did:

1.  I set the new drive to slave, connected it and used [hdclone (free)]("http://www.miray.de/products/sat.hdclone.html#free") to do the copy.  It took 22 hours (the free version is not "optimized" for speed or external drives).
2.  After setting the new drive to master moving the new drive to the correct position on the IDE cable, I used [these instructions]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") to boot to with a Kubuntu Live CD and but Grub back into working order.

I was so happy I had a new bigger drive without reinstalling and reconfiguring everything!

---

### Post by Frank Golden on 2006-07-15
I just love it when a plan comes together.:p

---

### Post by Frank Golden on 2006-07-15
I just love it when a plan comes together.:p Way to go tabinin=D>

---

