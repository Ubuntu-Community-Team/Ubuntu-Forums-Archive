---
title: "Dual boot questions"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-05
I was just wondering, in buying a second harddrive for my tower.

1. If my (asus k8n-e deluxe) mobo **supports dual raid** 6xSATA does that mean i can have 6 HD's or 2? 

2. Is it **easier or harder** to create a dual boot system?

3. **If anyone has** a dual boot system using 2 seperate HD's and has tips, **or** links it would be appreciated

4. My current **XP OS is using** the **NFTS** file system, will this create a problem

5. What's the deal between NFTS and FAT32

Anyone who can answer any,some, or all of these quetions I would muchly appreciate it, **thanks** in advance

cheers,
ad

---

### Post by amohanty on 2005-12-05
I have an Asus A8N + 2 SATA, however I dont use the onboard RAID. The way I set it up was
HDD1 - partition 1:  NTFS (windows)
          - partition 2:  ext3  (/boot)
          - partition 3: ext3 (/)

HDD2 - partition1: swap
           - partition2: /home

afaik NTFS does not create any problems, just that linux support is still immature so it is advisabe to mount it as a read-only volume in ubuntu.

Just make sure that you install windows first, on the first partition of the first/primary hdd, and then the ubuntu installer will do the rest for you.

HTH
AM

---

### Post by adduds on 2005-12-05
[QUOTE=amohanty]I have an Asus A8N + 2 SATA, however I dont use the onboard RAID. The way I set it up was
HDD1 - partition 1: NTFS (windows)
- partition 2: ext3 (/boot)
- partition 3: ext3 (/)

HDD2 - partition1: swap
- partition2: /home[/QUOTE]

This is what I thought was a good thing to do, I don't know if I'm right(probably not) but, have Windows on hda1 and Ubuntu on hda2? 

1. Why is their 3 partitions on hda1? 

2. Why don't you use RAID? 

3. Do I have to partition some of the hda1 to create a dual boot system? 

4. how come their is an ext3 (/boot) and just a (/)

Sorry I'm quite new...

---

### Post by adduds on 2005-12-05
no ones?

lol

c'mame you're all smart

---

### Post by amohanty on 2005-12-05
> 1. Why is their 3 partitions on hda1?

No specific reason, just went that direction, simeply because I wanted my /home on a separate drive with nothing else on it.

> 2. Why don't you use RAID?

Dont feel the need to. With two drives I can only use RAID0 (striped) or RAID1 (mirrored). Although both have their advantages, they were not sufficiently advantageous for me to use it. Just a personal preference.

> 3. Do I have to partition some of the hda1 to create a dual boot system?

No. As long as Windows is on the first partition of the primary master hard drive you are fine. You can install windows on the second hdd too but that requires a bit more configuration in the grub menu.lst file.

> 
4. how come their is an ext3 (/boot) and just a (/)

Again it was personal preference. I like to keep my /boot separate mostly for recovery reasons. You dont have to. This model has worked well for me in the past so I just tend to follow it. Other partitioning strategies will work just as well. I was just giving you an example of how I have done it.

> This is what I thought was a good thing to do, I don't know if I'm right(probably not) but, have Windows on hda1 and Ubuntu on hda2?

This is perfectly all right. Just make sure that GRUB is installed in the MBR then.

HTH
AM

---

### Post by Gray. on 2005-12-05
Most newbie friendly install would be:
HD One = Windows
HD Two = Ubuntu/Ubuntu Swap

Though you may find that a small (1 or 2GB) FAT32 partition on either hard drive would be good for when you wish to transfer files from Windows to Ubuntu (and vice versa). For example:
**Hard Drive One:**
198GB - Windows XP (C: drive)
2GB - FAT32 Partition (for transferring files)
**Hard Drive Two:**
248GB - Ubuntu
2GB - Linux Swap

Hopefully that makes sense to you. If you don't understand anything feel free to tell me so. :P

---

