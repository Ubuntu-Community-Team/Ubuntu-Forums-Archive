---
title: "EMERGENCY! - MacBook Pro won't boot after removing Ubuntu"
date: 2010-04-01
forum: Apple Hardware Users
---

### Post by ChristopherSu on 2010-04-01
I have a MacBook Pro (unibody, 5,4). I first installed Ubuntu (lucid, 10.04) with rEFIt. Wanting the disk space back (and being the idiot that I am) I deleted the Ubuntu partitions using Disk Utility in Snow Leopard. Everything was going fine and still working until I turned my MacBook Pro off. When I tried to turn it back on it showed:
```
error: no partition found
grub rescue>
```

I've tried various commands in grub rescue and none have worked so far except ls. I booted off my Ubuntu CD and it only showed a blank hard drive. I've been Googling for a solution for the past hour and I've tried everything. I tried resetting my PRAM. I can't locate my Snow Leopard DVD but I might be able to get one from a friend. I'm downloading DiskWarrior as I write this (to hopefully recover the data, forgot the operating system, I want my data back!).

Objective: get my data back (maybe onto an external hard drive?) so I can wipe everything and reinstall Snow Leopard. Even better: maybe get my Snow Leopard to work again without having to wipe and reinstall?

---

### Post by linuxopjemac on 2010-04-01
**This is a good lesson that you always backup data before doing things like this. I can recommend clonezilla for copying complete partitions and carbon copy cloner for OSX data.**

That said, I think you can rescue your drive by deleting grub from your MBR. From the liveCD do this:

```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

This will clear the MBRs' boot codes.
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18)
[B]
BE SURE THAT /dev/sda is your hard drive[/B]

---

### Post by ChristopherSu on 2010-04-01
> **linuxopjemac said:**
> **This is a good lesson that you always backup data before doing things like this. I can recommend clonezilla for copying complete partitions and carbon copy cloner for OSX data.**

That said, I think you can rescue your drive by deleting grub from your MBR. From the liveCD do this:

```
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
```

This will clear the MBRs' boot codes.
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18)
[B]
BE SURE THAT /dev/sda is your hard drive[/B]
Thanks for your reply! I hope there is still a way to retrieve my data.

How can I tell whether or not /dev/sda is my hard drive? I would just go ahead and run the command but I'm a bit cautious after what happened last time I did something without checking first. What would happen if I ran the command and /dev/sda wasn't my hard drive? As you wrote "BE SURE THAT" in caps I would assume something bad would happen.

When I boot from the liveCD in "Places"it shows a drive (can't recall the name, I'll check later but was like dev#sda#). Oddly enough this **drive was completely blank**. Is this my Mac drive (Previously known as "Macintosh HD")?

When I was on Snow Leopard (before I turned my computer off for the last time) Finder showed both Macintosh HD AND dev#sda#. Macintosh HD reflected the correct amount of free space and space (~215 GB, I gave 32 GB to Ubuntu). Oddly enough, the dev#sda# drive showed 250.06 GB (my entire drive size).

I can't find my Snow Leopard DVD but I tried booting off my Leopard DVD and it got stuck at the alt-option screen every time I tried to boot off the CD.

---

### Post by linuxopjemac on 2010-04-01
If you have no other drives attached (firewire, USB and the like), then that is the one...

---

### Post by ChristopherSu on 2010-04-01
I tried that. Here's the result:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
1+0 records in
1+0 records out
440 bytes (440 B) copied, 1.30507 s, 0.3 kB/s
ubuntu@ubuntu:~$ 
```

I then tried booting while holding alt-option and now **NO BOOTABLE DRIVES APPEAR**. This is bad.

When I boot without holding down alt-option I see a flashing folder with a question mark.

---

### Post by linuxopjemac on 2010-04-01
I think your partition table is nuked....

---

### Post by linuxopjemac on 2010-04-01
Maybe you can do things with a liveCD with TestDisk in it:
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Apparently your Ubuntu liveCD should have it...I have never tried it though.

Let us know how it works...

---

### Post by nerdy_kid on 2010-04-01
the first thing i would do if backup the whole drive, so at least you can experiment without worries on the real drive.

run

```

sudo dd if=/dev/sda of=EXTERNAL_DRIVE_MOUNT_POINT/file.img  bs=4M

```


take a good look at
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by ChristopherSu on 2010-04-01
> **linuxopjemac said:**
> I think your partition table is nuked....

In that case, should I be able to fix the partition table, will I be able to access all of my previous data?

I'm checking out TestDisk right now. I'll let y'all know if it works out.

---

### Post by ChristopherSu on 2010-04-01
> **nerdy_kid said:**
> the first thing i would do if backup the whole drive, so at least you can experiment without worries on the real drive.

run

```

sudo dd if=/dev/sda of=EXTERNAL_DRIVE_MOUNT_POINT

```


take a good look at
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

How would I go about backing up the entire drive? When I boot off the liveCD all I see is a drive named "disk0s2" (or something similar) that is completely blank.

---

### Post by ChristopherSu on 2010-04-01
I'm sort of confused now. I tried running TestDisk but apparently it doesn't come with Ubuntu (or at least not 10.04). When I tried to run it in terminal (sudo testdisk) it said command not found. I tried installing it using alien (following the instructions at [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)) but it failed as I don't have the drivers for the MacBook Pro's airport installed (and you can't install those without internet).

Any other suggestions? I'm planning on trying out DiskWarrior to recover my data. The problem is, I can't find my Snow Leopard DVD so I wouldn't be able to wipe and reinstall after recovering my data...

---

### Post by linuxopjemac on 2010-04-01
nerdy_kid is right. Just copy block for block (it's the same as clonezilla does). It does not matter if gparted sees it as an empty disk. At least you can then experiment on it. If it does not work, you can try again by copying back block for bock what you had before experimenting.

---

### Post by linuxopjemac on 2010-04-01
I would try Knoppix liveCD:
[http://www.cgsecurity.org/wiki/Damaged_Hard_Disk#Booting_from_Knoppix.2C_a_Linux_LiveCD](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk#Booting_from_Knoppix.2C_a_Linux_LiveCD)

---

### Post by ChristopherSu on 2010-04-01
> **linuxopjemac said:**
> nerdy_kid is right. Just copy block for block (it's the same as clonezilla does). It does not matter if gparted sees it as an empty disk. At least you can then experiment on it. If it does not work, you can try again by copying back block for bock what you had before experimenting.

Alright, thanks for all the help guys. I'm going to sleep tomorrow but tomorrow I won't be going down without a fight!

---

### Post by ChristopherSu on 2010-04-01
I'm sort of lost now. What exactly should I do? I just want to be able to use my MacBook Pro again and have my data still there...

---

### Post by linuxopjemac on 2010-04-02
Have a USB drive with enough space. Download Clonezilla and backup your whole hard disk. You can, if you want put the whole stuff back later. You can try with open source repair software first. I would try Knoppix or something, try to do testdisk.

---

### Post by ChristopherSu on 2010-04-02
Alright, I've got an external hard drive with ~350 GB left (and my entire internal HD space is only 250 GB). I'm checking out Clonezilla now. I have to go pick up some more CDs so I can burn more bootable stuff (like Knoppix).

---

### Post by ChristopherSu on 2010-04-02
I downloaded Clonezilla (the live CD) and I have no clue now to burn it to a DVD. It's a folder filled with folders. Do I just burn the folders on?

Edit: Nevermind, I downloaded the zip no the iso.

---

### Post by ChristopherSu on 2010-04-02
Tried using Clonezilla. It made a folder on my external HD that was 2.7 MB. Something doesn't seem right...

---

