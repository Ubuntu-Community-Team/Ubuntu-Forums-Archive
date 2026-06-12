---
title: "Windows Boots fast than ubuntu"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-03-26
hi all

ive heard a lot of people say ubuntus boot really fast but i dont see it. When it boots up it sits on 'Mounting root filesystem'  for 2 and 1/2 minutes. personaly i think thats too long.

some points:
-my system is 2.6 GHz with 512MB RAM
-Dual boot it with Windows
-3 HDD. 1 is linux(fat) the other 2 are Windows(ntfs)

and also 2 month ago i found a good artical about speeding up your machine. But i cant find it any more. it was good so if any one know of it please tell be.

ta,
Nolander.

---

### Post by psyberpnk on 2007-03-26
There are some suggestions in this article that might help,

[http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html](http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html)

---

### Post by zombiepkx on 2007-03-26
Well,
Linux is most efficient on ext3 Filesystems,

I've Had linux installed on fat partitions, and ext2 partitions, and I don't think there's really an actual FACT that it IS slower, but I noticed a large increase in performance when I reformatted to ext3 :)

---

### Post by Nolander on 2007-03-26
Thanx psyberpnk for that link.

is there any way to speed up the boot time without reformatting??

ta,
nolander.

---

### Post by dasunst3r on 2007-03-26
If your hard drive stopped accessing like mad mid-way through the boot process, then the 2 1/2 minutes you are waiting is when it is trying to obtain a network address, Windows 98 style.  If you are using a laptop, I suggest installing *network-manager-gnome* and its dependencies.  Then, edit your */etc/network/interfaces* file to look like this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```
That is, put '#' at the beginning of every line except for the last one.  Restart, and hopefully, it will be to a faster system. :)

I got my boot time down toe 30s.

---

### Post by rich.bradshaw on 2007-03-26
Why did you decide to install Linux on a FAT filesystem?

---

### Post by Nolander on 2007-03-26
a mate of mine!

he uses red hat dont no if redhat uses ext3 or fat??

should i injure him??

Nolander.

---

### Post by chocbar31 on 2007-03-26
I used to dual-boot also. Linux, nor myself appreciated the performance loss as a result of that configuration. Any type of "mounting" in Linux really sucked.

What worked best for me was to just install Ubuntu, get VMware Workstation Beta and put Winblows there. Everything is happier and snappier for me.

If you can, get a second HDD and benchmark the two configurations. And, don't use FAT...use default ext2 (Linux FS)! That's how I got over the same thoughts about the boot speed! They seem to be about the same to me.

---

### Post by macogw on 2007-03-26
Nah, they usually all use ext2 or ext3 by default.  He probably did it because Windows can read FAT so then you can see your files.  I'd just put the Linux system stuff on ext3 and Windows on its NTFS then make a separate partition to hold your files.  That should be either FAT32 or EXT3.  FAT32 can't hold files bigger than 4GB and can't go over a certain size.  EXT3 has drivers for Windows, though, and it doesn't fragment like FAT.


dasunt3r: 22 seconds here, i win :p

---

### Post by brennydoogles on 2007-03-26
I am having a similar problem on a recent dual boot system I set up. I'm wondering how much of it has to do with installing Ubuntu on a slave drive, because I have 3 dualbooted computers, and the only one that is having problems at boot-time is the one that has Ubuntu on the slave.[ Here]("http://www.ubuntuforums.org/showthread.php?t=393112") is the link to the thread I started about the same thing. Have a great day!

---

### Post by camz on 2007-03-26
If possible, you should try to have Ubuntu on ext3 format, not FAT.

---

