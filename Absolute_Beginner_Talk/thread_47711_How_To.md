---
title: "How To?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-09
im downloading the ubuntu linux, im gonna test it first on my vmware workstation and then if I liked it im gonna install it as my main OS...

but I have a question:
I have 2 partitions: c:\ and d:\
winxp is installed on c:\ and I don't care if that partition gets formated, but I do care about my d:\ drive becoz all of my mp3s are there.
so what should I do to install ubuntu linux withouth messing with my d:\
or can I install ubuntu with xp at the same time?

---

### Post by Kvark on 2005-07-09
You can have both ubuntu and windows on C:\.

First defrag your windows partition to make sure no data is in the end part of the partition. Then when you install ubuntu you can resize the windows partition to make room for a new partition.

I would say backup first because any data that is in the part you cut off (shouldn't be any, defrag moved it to thogether in the first portion of the partition) is destroyed, but you don't care so ok.

The installer can also set up grub for dual booting windows/linux.

Or you can go with default, which means the installer takes the whole drive for linux.

To tell them apart. C: is the first one, lowest one, HD1 or whatever, D: is the next one, highest one, HD2 or whatever.

edit: I am assuming the two partition C and D are on separate physical drives, if they are on the same drive. Don't do default!

---

### Post by Snitz on 2005-07-09
I really don't care about my drive c:
but I don't want to touch my drive d:

so what do I really have to do?
coz I didn't quiet understand!

---

### Post by dollydoll on 2005-07-09
[QUOTE=Kvark]You can have both ubuntu and windows on C:\.

First defrag your windows partition to make sure no data is in the end part of the partition. Then when you install ubuntu you can resize the windows partition to make room for a new partition.

I would say backup first because any data that is in the part you cut off (shouldn't be any, defrag moved it to thogether in the first portion of the partition) is destroyed, but you don't care so ok.

The installer can also set up grub for dual booting windows/linux.

Or you can go with default, which means the installer takes the whole drive for linux.

To tell them apart. C: is the first one, lowest one, HD1 or whatever, D: is the next one, highest one, HD2 or whatever.

edit: I am assuming the two partition C and D are on separate physical drives, if they are on the same drive. Don't do default![/QUOTE]
 How do I know which drive is HD1 , HD2, etc?
I have one 80Gb C drive w/ Win XP
another 120Gb partioned, so that I can install Ubuntu in one of the partitions, and 
a small 8 Gb drive w/ Linux Suse 9.2
When setting up the boot order with GRUB how do I know which drive is HD1 , HD2, etc?
many thanks

---

### Post by Kvark on 2005-07-09
No matter what you use to identify the drives, letters, numbers or something else, they are in the same order, so the one with the lowest number is the one with the lowest letter. (It is probably possible to get it the other way around if you partition in a weird way when installing windows, but doubt anyone would do that.)

Snitz:
Are C and D two different partitions on the same physical hard disk or are they two separate physical hard disks?

---

### Post by Snitz on 2005-07-09
[QUOTE=Kvark]No matter what you use to identify the drives, letters, numbers or something else, they are in the same order, so the one with the lowest number is the one with the lowest letter. (It is probably possible to get it the other way around if you partition in a weird way when installing windows, but doubt anyone would do that.)

Snitz:
Are C and D two different partitions on the same physical hard disk or are they two separate physical hard disks?[/QUOTE]
 C and D are two different partitions on the same physical hard disk!

---

### Post by dollydoll on 2005-07-09
aight...this is wat I have
Physical Drive C: (80Gb) NTFS 1 big partition w/ Win XP
Physical Drive 120Gb paritioned FAT32 as follows:
Logical drive:   L: 30Gb where I wanna install Ubuntu
Logical Drive:   S:  T: U: 30Gb each FAT32 that i would like to share between Linux and Win
Physical drive:  8Gb No letter since Linux Suse is there

I hope this gives you a better picture of what I have in my pc
regards,

---

### Post by Kvark on 2005-07-09
[QUOTE=Snitz]C and D are two different partitions on the same physical hard disk![/QUOTE]

Then back up D before you install, just to be safe.

What you need to do is either shrink or remove/replace C with the installer or with a partitioning tool. So don't choose the default partition option.

You should be fine if you defrag C first. And don't shrink it by more then there is free room for.



dollydoll: wow, thats a lot of partitions, confusing... Leave the 30gb ubuntu should have ubpartitioned before you install, and tell the isntaller to use the free space on the secound physical drive.



Hmm, someone should confirm this.

---

### Post by Snitz on 2005-07-09
[QUOTE=Kvark]Then back up D before you install, just to be safe.

What you need to do is either shrink or remove/replace C with the installer or with a partitioning tool. So don't choose the default partition option.

You should be fine if you defrag C first. And don't shrink it by more then there is free room for.



dollydoll: wow, thats a lot of partitions, confusing... Leave the 30gb ubuntu should have ubpartitioned before you install, and tell the isntaller to use the free space on the secound physical drive.



Hmm, someone should confirm this.[/QUOTE]
 > What you need to do is either shrink or remove/replace C with the installer or with a partitioning tool. So don't choose the default partition option.

You should be fine if you defrag C first. And don't shrink it by more then there is free room for.
I will defrag C:\ and install ubuntu right away
will that do the job?
im sorry im confused a bit

---

### Post by Kvark on 2005-07-09
[QUOTE=Snitz]I will defrag C:\ and install ubuntu right away
will that do the job?
im sorry im confused a bit[/QUOTE]

Yes, that will work, but whatever you do, don't go with the default partition option (to take the whole physical drive).

---

### Post by Snitz on 2005-07-10
[QUOTE=Kvark]Yes, that will work, but whatever you do, don't go with the default partition option (to take the whole physical drive).[/QUOTE]
 if I went with the default partition option will it take over drive c and d at the same time or just c?

---

### Post by Kvark on 2005-07-10
[QUOTE=Snitz]if I went with the default partition option will it take over drive c and d at the same time or just c?[/QUOTE]

It would take the whole physical drive I think, so if they are on the same drive then yes.

---

### Post by Snitz on 2005-07-10
ohhhhh
that sucks
which means I have to get partitionmagic and create a new space on my drive c to ubuntu gets installed on it?

---

### Post by Kvark on 2005-07-10
[QUOTE=Snitz]ohhhhh
that sucks
which means I have to get partitionmagic and create a new space on my drive c to ubuntu gets installed on it?[/QUOTE]

Yes, it means you have the either shrink or remove C. You can do that either with partition magic or with the install program. If you are used to partition magic then thats the best option.

Then you need to tell the installer to make a new partition on the free space.

---

### Post by Snitz on 2005-07-10
[QUOTE=Kvark]Yes, it means you have the either shrink or remove C. You can do that either with partition magic or with the install program. If you are used to partition magic then thats the best option.

Then you need to tell the installer to make a new partition on the free space.[/QUOTE]
 i'm not really used on partition magic!!
but i'll try it

> Yes, it means you have the either shrink or remove C
if I didn't use partition magic, ubuntu will format C and take over it
but I guess you said that ubuntu will take over both C and D if I didn't use PM

---

### Post by sooqing on 2005-07-10
there is no need to defrag, partition magic, etc..

just tell ubuntu to install on hda1 (c:)

btw, if u really want to resize, use bootit instead of partition magic, this FREE software (for windows) is a real gem even for resizing NTFS..  :)

---

### Post by Snitz on 2005-07-10
I  finally got partition magic, resized drive C (20GB) and made a partition called G (8GB) for ubuntu and installed it!

but the question is, how can I read/write on my other drives C and D?
all my mp3s are on drive D and i would like to access them using ubuntu?
how to?

---

