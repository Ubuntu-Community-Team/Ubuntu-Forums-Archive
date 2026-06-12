---
title: "Deleting and resizing partitions - XP and Feisty"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2007-06-05
Hello, 

I have a 40GB hard drive, and there are 4 partition on it:

First one is Windows (C:\). The windows root. It's NTFS
The second one is also for windows (D:\). I store pictures, music, videos here. It's NTFS too.
The third one is for linux, mounted as /, and it's ext3
And the fourth one is swap for linux

Now, I have bought myself a shiny new hard drive and inserted it as a slave drive. I've formatted it to have one partition, which is K:\ on windows and it's NTFS.

What I want to do now: 
I want to delete the second partition of the first hard drive and extend Windows' and linux's partition over the free space; use the new hdd for files which were on that partition.

However, this brings some questions...
How will Windows react to one partition suddenly disappering?
Hos safe is it to extend both root partitions? One of them is where GRUB sits!
What is the chanche of not even being able to boot after this?

Also, what should I use for this operation? gParted LiveCD or gParted while having booted Ubuntu? Are there any more things I should consider before proceeding?

Thanks, 
Klaidas

---

### Post by Crafty Kisses on 2007-06-05
> **Klaidas said:**
> Hello, 

I have a 40GB hard drive, and there are 4 partition on it:

First one is Windows (C:\). The windows root. It's NTFS
The second one is also for windows (D:\). I store pictures, music, videos here. It's NTFS too.
The third one is for linux, mounted as /, and it's ext3
And the fourth one is swap for linux

Now, I have bought myself a shiny new hard drive and inserted it as a slave drive. I've formatted it to have one partition, which is K:\ on windows and it's NTFS.

What I want to do now: 
I want to delete the second partition of the first hard drive and extend Windows' and linux's partition over the free space; use the new hdd for files which were on that partition.

However, this brings some questions...
How will Windows react to one partition suddenly disappering?
Hos safe is it to extend both root partitions? One of them is where GRUB sits!
What is the chanche of not even being able to boot after this?

Also, what should I use for this operation? gParted LiveCD or gParted while having booted Ubuntu? Are there any more things I should consider before proceeding?

Thanks, 
Klaidas

To be honest you should use the LiveCD, but that's just me, I would not use PartiotionMagic.

---

### Post by LaRoza on 2007-06-05
> 
However, this brings some questions...
How will Windows react to one partition suddenly disappering?
Hos safe is it to extend both root partitions? One of them is where GRUB sits!
What is the chanche of not even being able to boot after this?

1. Windows won't care if a partition disappears.

2. Resizing a partition with an OS will not affect the OS as long as everything works during the resizing. GRUB will not move.

3. The chance of not being able to boot after this is low, even if something goes wrong, if you do have trouble, use the Super Grub Disk. 

The Super Grub Disk is a very useful booting tool, it works with Windows, including Vista, Linux and others, it can be used to restore the MBR for Windows and much more. It is basically, er, a Super Grub Disk.

Here is a mirror:  [http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

I would use the GParted LiveCD.

---

