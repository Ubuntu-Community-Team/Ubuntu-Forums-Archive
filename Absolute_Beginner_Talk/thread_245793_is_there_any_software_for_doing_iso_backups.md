---
title: "is there any software for doing iso backups"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by peav007 on 2006-08-28
i was just wondering if there's any software of making iso back ups of my original disk to save them getting damaged..

some thing on the lines of ultra-iso or win-iso it doesn't matter if there isnt i just have to be careful not to damge my disks

tia  john:p :p

---

### Post by aysiu on 2006-08-28
K3b?

---

### Post by peav007 on 2006-08-28
cheers for that. but i mean copying a disk or dvd to form an iso file then burning it. so i can presserve my original disk.

i know i can burn iso files with k3b.

i want to be able to put a software disk into the drive then create an iso image of that disk.then burn it as an iso file for better backup

tia john:-D

---

### Post by aysiu on 2006-08-28
Yes, and you can do that with K3B. Select the "copy disk" option and then instead of making an actual copy, in the dialogue that pops up, select that you want to create the image only.

---

### Post by VirtuAlex on 2006-08-28
you can use dd if you're not afraid of command line

---

### Post by orb9220 on 2006-08-28
If you just want to backup a non-protected disc.

Just insert right-click copy disc amd when dialog pops up at the top is copy disc to: change that to file image then write and a location dialog will popup and tell it where you want to save.

---

### Post by peav007 on 2006-08-28
many thanks to all for the info , as you can proberly gather im new to ubuntu,


what is the disk is copy protected #???     


tia  john:p :p :p

---

### Post by orb9220 on 2006-08-28
Game discs and some audio cd and movie dvd's have copy protection on them as to defeat the process of making copies of the disc's.

---

### Post by peav007 on 2006-08-29
so theres no way of copying these type of disks then??

while on the suject of backing up is there any software to get around this..
and also is there any imaging software that backs up linux. something on the line of ghost or trueimage, so once i get my system to how i want it save to an image incase of any disaster,,,

 cheers john:mrgreen: :mrgreen:

---

### Post by peav007 on 2006-08-29
any body got any more info...

cheers john:-k :-k

---

### Post by VirtuAlex on 2006-08-29
> **peav007 said:**
> so theres no way of copying these type of disks then??

while on the suject of backing up is there any software to get around this..
and also is there any imaging software that backs up linux. something on the line of ghost or trueimage, so once i get my system to how i want it save to an image incase of any disaster,,,
It's all done with dd. Simple but powerful. It takes any partition (HD, CD, floppy, etc.) and writes its image into a file, or other way around (except it does not burn cd's, you have to use other tools like cdrecord for that). Basically iso file is just an image of a partition on cd drive. There is also dd_rescue which intended to rescue damaged partitions but can take care of copy protection based on "bad sectors" as well. So, want to "hack" your cd's? Learn command line. It's not that scary after all.

---

