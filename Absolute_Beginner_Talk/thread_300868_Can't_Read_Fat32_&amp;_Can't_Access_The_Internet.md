---
title: "Can't Read Fat32 &amp; Can't Access The Internet"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Ixon on 2006-11-16
Hey everyone!

Not sure if I'm posting this in the right section. But I'm like extremely new to Linux, I just got my Ubuntu CD's yesterday and I'm  have some small issues here and there. 

1) I searched these forums and learned that Ubuntu can read FAT32, so I took my Library drive, which is where I store all my music, photos, movies and work files and documents - and converted it from NTFS to FAT32. Just so I can have a seamless interaction between both O.S's (Windows - Ubuntu) with all my files. 

Well, I thought wrong - every time I try to mount the partition in Linux, I get this exact error.

Error: device dev/hda2 is not removable
Error: could not execute pmount

I've searched the forums a number of times for solutions and nothing has worked from what I've found, unless I'm doing something wrong. A step by step guide might ease the pain a bit! 


2) Well my second issue is I can't connect to the internet. I live in a rural area where dial up is the only type of internet access. And when I try to configure my connection in Ubuntu, it will not activate or work - At all.

Again I searched these forums and discovered there is some issues with the PC-Tel Platinum V.90 modem. I downloaded the driver on my windows partitions. But that's as far as I can go because I can't access my Library drive from Linux. 


So basically, I'm in a dead end situation here, please help a newbie in need! lol.

Later guyz.

---

### Post by podunk on 2006-11-16
Ah, what exactly is a Libray drive? Is this a brand name? A quick search on goggle returned a bunch of stuff about tape drives of various sorts - that's not what this is is it?

Folks will find the output from
```
sudo fdisk -l
```
very helpful, as well as copying the file that is opened by
```
gksudo gedit /etc/fstab
```

For the driver - can you burn it to a cd? Or a floppy?

---

### Post by anaconda on 2006-11-16
Sounds like you are trying to mount a fixed disk (hda) with pmount, so ofcourse it wont work. (pmount is for removable devices.)

You can either mount it manually from terminal, or add a line to your /etc/fstab -file to mount it automatically each time you boot your machine..

here is how you can do it manually:
```

sudo mkdir /library
sudo mount -t auto /dev/hda2 /library
```

After running these two commands your hda2 should be mounted and accesible from /library -folder. Default is that only root can access the new directory, so you can do this in terminal:
```
sudo chmod a+rwx /library
```

or access the drive by opening nautilus with root (admin) rights
```
sudo nautilus
```

and to your 2.nd problem:
are the drivers you downloaded meant for ubuntu or windows?
windows drivers wont work directly, but some of them can be used using ndiswrapper.

---

### Post by bodhi.zazen on 2006-11-16
For a fat partition yoy should use umask as an option to set permissions.

```
sudo mount -t auto /dev/hda2 /library -o umask=000
```

Or add an entry to [/etc/fstab](http://ubuntuforums.org/showthread.php?p=1653968#post1653968)
```
/dev/hda2 /library vfat auto,users,umask=000 0 0
```

---

