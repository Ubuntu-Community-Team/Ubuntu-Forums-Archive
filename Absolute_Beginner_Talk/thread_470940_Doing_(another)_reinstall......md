---
title: "Doing (another) reinstall....."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-06-11
I'm having a blast with Ubuntu, experimenting and learning..... and of course, this can lead to really goofing things up..... so I'm going to start over.....
...which leads me to a partitioning question....

My laptop is a Presario 2170us with an ATA 40g hdd.

I have WindowsXP on my C: partition, my CD/DVD drive is D:, and a FAT32 parition is E: (for sharing with Ubuntu).

I'm figuring for sizes:
c: - 10 gig
E: -  6 gig

....which leaves 24 gig for Ubuntu.

I've been reading about creating a separate **/home** parition so a change can be made in the Linux OS without affecting **/home**, which sounds like a great idea.... 

so I'm thinking these hdd sizes for Ubuntu:
Home - 10 gig
Linux  - 13 gig
Swap  - 1 gig

Do these sound right?  Or should I take another approach?

Thanks!

---

### Post by p_quarles on 2007-06-11
Sounds good to me. Of course, you can also always backup your /home folder to a USB drive or DVD, for much the same effect.

---

### Post by TriggerHappyChewie on 2007-06-11
I would make your Linux partition substantially smaller whilst making your home partition bigger.

---

### Post by Najand on 2007-06-11
Home - 10 gig
Linux - 13 gig
Swap - 1 gig
Sounds good.

---

### Post by Inxsible on 2007-06-11
I would reverse home to 13GB and root to 10 GB. Swap of 1GB is perfect.

---

### Post by Inxsible on 2007-06-11
The other thing you could do is, merge the home and the E: together. you will then have 19GB for the home partition. You can use [FS-Driver]("http://www.fs-driver.org") to read and write to the EXT3 partition (/home) in Windows.

---

### Post by ElEdwards on 2007-06-12
I have finished the reinstall with the following:

Home  14 gig (ext2)
Root    10 gig (ext3)
Swap    1 gig 

....but I have a question:
Even though **/home** is a separate partition, when I use File Browser and look in *File System*, **home** is a folder there.  Is this correct??

I can right click on this **home** folder and the Volume is **/home** and it shows the correct Free Space (13.8 Gig).

If it's correct, I did it right! :)
....but if not, please tell me where I went wrong. :(

I guess for some reason, I was expecting **/home** to show up separately from everything else.

Thanks! :)

---

### Post by Najand on 2007-06-12
Sure it is OK.After all, /home is a directory under root filesystem ("/").

---

### Post by Inxsible on 2007-06-12
> **ElEdwards said:**
> I have finished the reinstall with the following:
 
Home 14 gig (ext2)
Root 10 gig (ext3)
Swap 1 gig 
 
....but I have a question:
Even though **/home** is a separate partition, when I use File Browser and look in *File System*, **home** is a folder there. Is this correct??
 
I can right click on this **home** folder and the Volume is **/home** and it shows the correct Free Space (13.8 Gig).
 
If it's correct, I did it right! :)
....but if not, please tell me where I went wrong. :(
 
I guess for some reason, I was expecting **/home** to show up separately from everything else.
 
Thanks! :)
Yes its correct. Unlike Windows, everything in Linux is a folder or file. Even though /home shows up as a folder, it is a separate partition.
 
Actually, you can also create folders as partitions in Windows. I mean, you can have a complete partition of C:\MyData, just that MS doesnt make it intuitive to allow users to do that easily.

---

### Post by ElEdwards on 2007-06-12
Whew!  I've been immersed in M$ Windows too long :)

Thanks for the support! :D

---

