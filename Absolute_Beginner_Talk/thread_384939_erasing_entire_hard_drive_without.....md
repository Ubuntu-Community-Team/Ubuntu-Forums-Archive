---
title: "erasing entire hard drive without...."
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-15
hey all i decided to erase my entire hard drive and just leave ubuntu as my windows dont exsist on the c drive anymore and i set the partition of linux to only 25gb.  is there a way to erase my hard drive and leave ubuntu without reinstalling ubuntu? in other words, id like to use my full hard drive instead of the 25gb of space i partitioned.

---

### Post by Najand on 2007-03-15
Install gparted using repositories:
```

sudo apt-get install gparted

```
Then try to remove your Windows Partition and resize the "ext3" partiton of windows.

---

### Post by noob_saioke45601 on 2007-03-15
ok so i just delete the NTFS parition of linux and resize ext3? here's all the partitions...

fat32 - but its for system recovery and only has 5.03gb of space. used space is 3.85gb
NTFS - 25.03gb 
ext3 - 26.50gb used space is 3.58gb
Extended - 729.51mb
Linux-swap - 729.48mb

also ext3, extended, and linux-swap are both locked so cant resize. and under NTFS which is winxp it has a warning icon which says unable to read the contents  of this filesystem. because of this some operations may be unavailable. did you install the correct plugin for this filesystem.

---

### Post by buuntuu! on 2007-03-15
you cannot resize a mounted (active) partition! if you want to resize your ubuntu partition you'd have to use the live-cd so your partitions are unmounted.
alternatively you could just leave your ubuntu-partition alone and format window$ to ext3,reiser...whatever filesystem you like, and use it as a separate partition.
read [psychocat]("http://www.psychocats.net./ubuntu/") on partitioning, very helpful.
have fun

EDIT: xp can't read your inux-partitions, because it does not recognize its filesystems, that's normal

---

### Post by noob_saioke45601 on 2007-03-15
ok so in other words i can just change the format from NTFS to ext3 and that space will be added to the ubuntu hard drive?

---

### Post by AtrejuT on 2007-03-15
no it's not that simple I'm afraid.

What I'd suggest doing is:
- delete the windows and recovery partitions
- make a new ext3 partition in their place
- boot from a live cd
- move everything in /home to your new partition
- set up fstab such that it is mounted to /home automatically

This is only a rough outline of what there is to do, but you can find the details all around the forums or ask again if you run into trouble.
Why do this? It is widely recommended, and IMHO really a good idea to have a separate partition for /home. That way, if you screw up your install, or you just want to do a clean reinstall or whatever, you can format the ubuntu partition, leaving your home well alone, reinstall ubuntu and just keep all your settings and files which are stored in /home.

questions? - just ask...
good luck,
atreju

ps\ it would be possible though, to boot a live cd, erase the win/recovery partitions and then resize your ubuntu partition to take up all the space, yes. I think having a separate partiton for /home is the better solution, though.

---

### Post by hyper_ch on 2007-03-15
Hmmm, may I suggest something:

I would make a "root" partition of about 10 GB and then make an additional "/home" partition with the rest of the space that you have...
This for the simply reason as user related documents and stuff is in "/home"... so when you want to reinstall ubuntu again or some other linux then you just reformat the root partition but you won't touch the "home" one :)

---

