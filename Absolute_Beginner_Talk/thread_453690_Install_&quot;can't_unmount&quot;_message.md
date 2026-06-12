---
title: "Install: &quot;can't unmount&quot; message"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by godssiren on 2007-05-24
Alright, so after trying out Ubuntu for a few weeks, I really like it and I want to install it. I have read every walkthrough I can find about mounting drives and about installs, and even bought the Ubuntu Guide Bible (pretty good book, great desk reference) but I can't find anything about my problem.

I tried to install, and I get through the language, time zone, keyboard selection sections... and on to the prompt for guided or manual disk partitioning.
I chose manual since I want to run a dual boot system.

I currently have:

sda1 NTFS (windows XP)                                                   Primary          ~35GB         boot
sda2 FAT32(recovery for XP)                                            Primary          ~5GB
sda3 FAT32(shared files for XP and hopefully Ubuntu)     Primary          ~20GB
sda4 -- (where I want to create Ubuntu and Swap)         Extended       ~15GB
             |-->(space unused)

I originally didn't have sda4, but I realized that I needed 2 partitions where only one primary was available. 

So I created the Extended partition to hold Ubuntu and the Swap partitions.
When I get to the partition prep screen, it won't let me continue unless I create an ext3 and swap partitions, so I did. I mounted the ext3 at / the first time. Then it goes on and lets me know that it is going to format the ext3 partition and shows a progress bar.  (Later even tried not mounting it, but it won't let me get to the next screen without a mount point)

But suddenly it stops and a little doalogue box pops up that tells me it could not unmount the drive and gives me the options to "go back" or to "continue". I have tried both. They both bring me back to the partition preparation screen without my ext3 or swap partitions created. 

Am I doing something wrong?
please let me know if I missed a post about this problem. I've not been able to figure out where I'm messing this one up and I'm pretty sure it's user error at this point.

---

### Post by ggaaron on 2007-05-24
Isn't any of your disks automounted? Or perhaps you are using this discs and they can't be unmounted?

---

### Post by calraith on 2007-05-24
Three things.  Firstly, extended usually starts at /dev/sda5.
/dev/sda1 = NTFS = /media/c
/dev/sda2 = FAT32 = /media/d
/dev/sda3 = FAT32 = /media/e
/dev/sda5 = swap
/dev/sda6 = ext3 = /

Next, NTFS support in Linux is pretty damn good now.  If you're keeping fat32 for Linux compatibility, there's no need.  Feel free to type use the "convert" command in Windows to convert the fat32 partitions to NTFS:
```
convert x: /fs:ntfs
```where "x:" is the drive letter you're converting (presumably D: and E:).  After you install Ubuntu, install the ntfs-3g driver.
```
sudo apt-get install ntfs-3g
sudo nano -w /etc/fstab
```and wherever you see "ntfs" replace it with "ntfs-3g."

Lastly, you can go to a terminal and umount devices that refuse to be umounted first by trying to remount read-only:
```
sudo umount -r mntpoint
```If that doesn't work, umount with the lazy switch:
```
sudo umount -l mntpoint
```Good luck!

---

### Post by godssiren on 2007-05-28
thank you for all your help. I set myself out to do this as I tried to install again. but this time, it just let me do it. no issues whatsoever.
I don't know what was wrong with it, but at least now I have a reference to unmount. 
This is officially my first post from within Ubuntu on my computer, instead of off the live CD! ^_^

---

