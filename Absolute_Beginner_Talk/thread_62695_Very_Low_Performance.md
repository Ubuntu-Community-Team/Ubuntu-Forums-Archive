---
title: "Very Low Performance"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by ssindia on 2005-09-05
Hello To all the Linux People,
I have never operated linux before and as soon as i received a copy of ubuntu CD of 5.04. today i decided to go for it.
 
I installed it on following system
P-4, 2.4GHz, 845 GVSR board.
128 MB ram.
I have opted to installl it with my existing XP pro SP2.
I have was having a unused partition of 4 GB which was created by data recovery software Restore IT, and installed it on it after formatting with software included in the CD. everything worked fine except that when i start ubuntu, it works nice initially,mouse pointer moves fine, but as soon as i open an apllication performance dips and suddenly in matter of seconds. system hangs.

I also like to know what should be the ideal file formatt fat, fat32 etc..
i reinstalled it twice with no improvement,

Now should i use little more spacious Hard DIsk or the problem is something else.
Please note that i have no knowledge of computer internals but can follow the simple installation documentations.
Thanks you
Thank you.

---

### Post by rafakl on 2005-09-05
its possible that it can be a graphic card problem....

whats your graphic card model????

---

### Post by Qrk on 2005-09-05
Did you remember to make a swap partition?

Thats the simplist explanation I can think of.

---

### Post by xequence on 2005-09-05
128 MB RAM isnt enough for gnome. Try xfce. Gnome runs slow on my 700 mhz with 192 MB RAM.

---

### Post by Kvark on 2005-09-05
[QUOTE=ssindia]128 MB ram.[/QUOTE]
That is a bit low, but not low enough to explain what you experience. Perhaps the swap partition has gone missing?

[QUOTE=ssindia]I also like to know what should be the ideal file formatt fat, fat32 etc..[/QUOTE]
Go for ext3, it doesn't fragment. Fat fragments a lot and ntfs fragments some as well.

---

### Post by az on 2005-09-05
[QUOTE=ssindia]
I also like to know what should be the ideal file formatt fat, fat32 etc..
i reinstalled it twice with no improvement,

Now should i use little more spacious Hard DIsk or the problem is something else.
Please note that i have no knowledge of computer internals but can follow the simple installation documentations.
Thanks you
Thank you.[/QUOTE]


When you installed, did you free up that 4 gig partition, or did you keep the existing data?  I ask because you cannot run Linux or unix on a fat or fat32 filesystem.  Those filesystems do not permit for file permissions and so forth.  Also, if you just used the partition by itself, you did not create a swap space - virtual memory which will pretty much be neccessary for a system with 128 megs of memory.

The proper way to install is to boot the install cd and get to the point where it asks you about partitioning.  You chose then to manualy edit the partition table.  You then select the 4 gig partition and you tell the partitioner to delete it.

You will then be shown the partition table with a chunk of free space.  Scroll down to "guided partitioning" and the installer will create two partitions of the proper type (take the default:  ext3 and swap)  Make it go and then prepare yourself some tea.

Is this more or less the way you installed?

---

### Post by ssindia on 2005-09-06
[QUOTE=azz]When you installed, did you free up that 4 gig partition, or did you keep the existing data?  I ask because you cannot run Linux or unix on a fat or fat32 filesystem.  Those filesystems do not permit for file permissions and so forth.  Also, if you just used the partition by itself, you did not create a swap space - virtual memory which will pretty much be neccessary for a system with 128 megs of memory.

The proper way to install is to boot the install cd and get to the point where it asks you about partitioning.  You chose then to manualy edit the partition table.  You then select the 4 gig partition and you tell the partitioner to delete it.

You will then be shown the partition table with a chunk of free space.  Scroll down to "guided partitioning" and the installer will create two partitions of the proper type (take the default:  ext3 and swap)  Make it go and then prepare yourself some tea.

Is this more or less the way you installed?[/QUOTE]

Thankx all of you. i did what azz said and its working streaming fast...
i have not made two partition and installed on the single one thats the reason for the error.
And as far as TEA is concerned AZZ i have installed windows many times and have to wait for much long than linux.
.

---

