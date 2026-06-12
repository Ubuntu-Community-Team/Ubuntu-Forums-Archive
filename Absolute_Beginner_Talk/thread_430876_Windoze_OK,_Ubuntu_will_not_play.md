---
title: "Windoze OK, Ubuntu will not play"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-05-02
Hi,

I am having problems with a memory stick duo.  It is 4gig and is for my phone.  I plug it into my card reader and insert into usb it is listed in places but Ubuntu will not mount it.  I have tried in the terminal also, output of dsmg (i think) tells me that it either has wrong fs type or bad superblock?  The odd thing is if i empty the contents of the card Ubuntu reads it fine.  In fact Ubuntu wrote all of the data onto the card, it wrote the data, i plugged it back into my phone to check, back into ubuntu and it would not mount again.   I am having to constantly boot back into XP all the time to write any data or remove data.  I might as well just boot into windoze all the time at this rate.
Any ideas anyone
The card reader seems fine as all my sd carda and other msduo seem to mount ok.

---

### Post by starcraft.man on 2007-05-02
Just a question, but if you take the SD card out and put it back in, or put it into windows and then put it back into Ubuntu does it mount fine? If the phone is the problem, maybe it modifies the files somehow when reading it, lots of hardware expect windows always >.>.

---

### Post by Campingman on 2007-05-02
> **starcraft.man said:**
> Just a question, but if you take the SD card out and put it back in, or put it into windows and then put it back into Ubuntu does it mount fine? If the phone is the problem, maybe it modifies the files somehow when reading it, lots of hardware expect windows always >.>.
It does mount the card every so often (or it did at one time), although it does not seem to want to mount it at all now.  I have another card which came with the phone and Ubuntu mounts it every time. In fdisk -l it shows the disk as FAT32.  I am just trying to sort out the command to mount it from terminal.

---

### Post by Campingman on 2007-05-02
I have found a work around,  I can mount the card via the terminal, bit of a pain all the time but a solution all the same.
Thanks

---

