---
title: "GRUB Error 22 / Partition Problems"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Rotodyne on 2007-02-23
Hello All,

I believe I deleted the partition that Ubuntu was on, so now Grub won't load. 
I have tried installing Ubuntu again, to allow me to boot into windows, but I can't get Ubuntu to install.

Right now my partition table looks like this:

#3 Primary 59.7 MB swap swap
#2 Primary 79.4 GB ntfs /media/sda2                      (windows)
#1 Primary 567.5 MB ext3 /media/sda2

The problem is that I can not split #2 into multiple partitions for some reason, I need to split it in order to create enough space to install ubuntu, in order to get grub.

When I try to create a new partition in #2, I put in a size, it gives no error but does not split it. :(

If there is anyway I can boot into windows that would be great :confused: 

THanks in advance

---

### Post by annda on 2007-02-23
if you have the windows install cd boot from that and choose recovery console instead of install. then type fixmbr.

also, how did you delete the ubuntu partition? do you still have unpartitioned free space on your disk? if so, you can create a new partirion there.

---

### Post by Rotodyne on 2007-02-23
I was using Partition Magic and removed all the info on my Ubuntu partition when I was on windows......bad move.

I made my windows partition larger, but now I can't split it 

Unfortunately my computer did not come with a Windows CD, I guess I will have to get one.

Why doesn't it let me split my largest partition? :confused:

---

### Post by annda on 2007-02-23
ok, this seems a bit tricky then.

tell us whether you would like to have ubuntu again, or whether you just want your windows back. then we can work on the best solution for you.

---

### Post by Rotodyne on 2007-02-23
I would just like Windows back :) 

Thankyou very much for all the help annda

---

### Post by annda on 2007-02-23
i'm not really helping yet, Rotodyne ;-)

the easiest way for you will be to borrow somebody's windows cd (not recovery cd!). don't worry, it is not illegal, since you will not be installing from it and you will not use their license key.

if you manage to borrow an xp cd, go to recovery console and type fixmbr.

a win98 system recovery floppy will do if you have a floppy drive, but then you will need format or fdisk command rather than fixmbr (can't remember which) to format the mbr and remove grub from the boot sector.

call your friends and ask for help - and REALLY, there is nothing illegal in that and microsoft won't be angry with you or whoever lends you the cd or floppy.

---

### Post by Rotodyne on 2007-02-23
Ok thanks, I'll go try to borrow an XP CD, I'll post back later if it was a success

---

### Post by Patrick K on 2007-02-23
Pre-made boot disk are available for many OS's. Do a google search and you should turn one up. They contain most all utilities you might need. You'll need to download it and copy it to a floppy. I expect they are available as an ISO for CD burning, although I personally haven't seen one. But then again, I haven't looked for one.

---

### Post by Rotodyne on 2007-02-23
> **Patrick K said:**
> Pre-made boot disk are available for many OS's. Do a google search and you should turn one up. They contain most all utilities you might need. You'll need to download it and copy it to a floppy. I expect they are available as an ISO for CD burning, although I personally haven't seen one. But then again, I haven't looked for one.

Unfortunately my computer has no floppy drive, and the only computer with burning abilities is the one that won't boot :( 

I'm going to try to borrow a CD from a friend, or have him burn me one

---

