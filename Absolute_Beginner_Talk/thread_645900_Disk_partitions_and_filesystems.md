---
title: "Disk partitions and filesystems"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by DaveBloor on 2007-12-20
I am going to install Ubuntu Server 7.10.

The machine in question has three physical disks in it, they are as follows.

120Gb
150Gb
500Gb

I am planning to install the server onto the 120Gb disk and let it automatically partition itself. Is this the best way utilise the disk or is there a better way?

The 150Gb I was hoping to use for running VMWare and actual VM's, what is the best way to partition this disk and what is the best file system to use?

The 500Gb disk will be used for data storage, music, video. What is the best file system to use for this disk.

Please bear in mind although I have used Linux on the desktop I have never manually partitioned anything so please be gentle !!!

---

### Post by The Cog on 2007-12-20
For the 120G, it is probably worth making 4 partitions:
10G ext3 for /
10G ext3 spare for / when testing the next OS release
2G swap 
rest /home
This allows you to install a new test OS and keep your home data and settings.

For the other two, I guess one ext3 partition each would do just fine.

---

### Post by Daveth on 2007-12-20
Welcome to the Ubuntu Forum

You'd best check these out first

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

---

