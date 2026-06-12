---
title: "Making partition bigger?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-10
Hi.,

I want to make my linux drive bigger. Can i do this my putting in the linux boot CD and then do like i did to make the linux partition and then just make the drive bigger ? Or is it possible at all?

---

### Post by bigken on 2007-07-10
use the gparted liveCd its easy

---

### Post by czepluch on 2007-07-10
> **bigken said:**
> use the gparted liveCd its easy

Okay thanks. But is is possible to do it, right?

---

### Post by bigken on 2007-07-10
as far as know yes try it cant hurt

have you searched the forum

---

### Post by beefcurry on 2007-07-10
there is gparted on the ubuntu live cd as well. Not that the gparted live cd is much different.

---

### Post by UnixAnt on 2007-07-10
Just out of interest, when you say 'linux partition' does that imply you are running your OS off a single ext3 partition and a single swap partition?

Assuming you have free space at the end of the drive, then you shouldn't have a problem.

---

### Post by davidjmayo on 2007-07-10
How are you going to make the partition bigger??

from free space?
From resizing a windows partition??

Backup your data just in case.

---

### Post by st0nes on 2007-07-10
And don't forget to defragment your Windows partition before you start (if you have dual boot).

---

### Post by davidjmayo on 2007-07-10
> And don't forget to defragment your Windows partition before you start (if you have dual boot).

That's why I was asking

---

### Post by czepluch on 2007-07-10
> **davidjmayo said:**
> How are you going to make the partition bigger??

from free space?
From resizing a windows partition??

Backup your data just in case.

I'm doing it from resizing a windows partition. So that i will make some freespace and then add it to my ext3 partition. That is possible right?

---

### Post by davidjmayo on 2007-07-10
Yes of course it's possible but before you resize the win partition do the defragment as per st0nes reply

Do the defrag a few times to make sure it's done properly then when you resize it shouldn't corrupt the win partition.

I stress again backup any data on that win partition to be safe

After your defrag resize the partition how you want (I recommend using the GParted Live CD over the Ubuntu Live CD)

---

### Post by UnixAnt on 2007-07-10
Definitely backup your data.  This most likely involves resizing the ntfs partition, moving the ext3 start boundary  to the beginning of the free space, then moving the ext3 end boundary to the end of the free space.

Risky, although straightforward.  Backup your data ;)

---

### Post by st0nes on 2007-07-10
A caveat:  if you are resizing your root partition, then you MUST do this from a live CD (either Ubuntu or Gparted) because you will have to unmount your root (/) partition to resize it.  (Don't panic, this will be done for you by the partition app.) While you are doing this, make another partition for /home.  This will allow you to reinstall or upgrade Ubuntu without putting your data in /home in jeopardy.

---

### Post by czepluch on 2007-07-10
> **st0nes said:**
> A caveat:  if you are resizing your root partition, then you MUST do this from a live CD (either Ubuntu or Gparted) because you will have to unmount your root (/) partition to resize it.  (Don't panic, this will be done for you by the partition app.) While you are doing this, make another partition for /home.  This will allow you to reinstall or upgrade Ubuntu without putting your data in /home in jeopardy.

I dont really understand. Now i've got 16GB free and unpartitioned space on my computer. How do i make my ubuntu drive bigger then. Or should i just make this as a new partition and use it for storing ?

---

### Post by st0nes on 2007-07-10
The Ubuntu default is to have only 2 partitions (/ and swap).  The problem with that is if you really screw something up badly and have to reinstall Ubuntu, you will lose all the data in /home.  So it's better to mount /home on its own partition.

If you have 16GB I would recommend:-

5GB root partition (/)
2GB swap partition (should be at least twice the size of your installed RAM.
9GB home (user) partition (/home)

---

### Post by czepluch on 2007-07-10
> **st0nes said:**
> The Ubuntu default is to have only 2 partitions (/ and swap).  The problem with that is if you really screw something up badly and have to reinstall Ubuntu, you will lose all the data in /home.  So it's better to mount /home on its own partition.

If you have 16GB I would recommend:-

5GB root partition (/)
2GB swap partition (should be at least twice the size of your installed RAM.
9GB home (user) partition (/home)

I've already installed ubuntu. But i want a place to store documents and stuff like that . And for that i've got 16gb free. So should i make a new drive from it or what should i do?

---

### Post by czepluch on 2007-07-10
What to do ?

---

### Post by davidjmayo on 2007-07-10
You can use the 16 GB as a data storage partition.

Remember though if you only have one hard drive and it fails you lose everything unless some recovery tool works or you go to the professionals (very expensive). Having a partition is not the same as having a second hard disc.

You still need to backup your data (both ubuntu and windows) regularly somewhere else - hard disc, CD/DVD, tape, online.....whatever

---

### Post by czepluch on 2007-07-10
> **davidjmayo said:**
> You can use the 16 GB as a data storage partition.

Remember though if you only have one hard drive and it fails you lose everything unless some recovery tool works or you go to the professionals (very expensive). Having a partition is not the same as having a second hard disc.

You still need to backup your data (both ubuntu and windows) regularly somewhere else - hard disc, CD/DVD, tape, online.....whatever

Okay. Thanks. What filetype should i make the drive ?

---

### Post by czepluch on 2007-07-10
Does anyone know that?

---

### Post by czepluch on 2007-07-10
Bump

---

### Post by bigken on 2007-07-10
ext3

---

