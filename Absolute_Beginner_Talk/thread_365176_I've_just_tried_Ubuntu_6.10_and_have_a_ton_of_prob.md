---
title: "I've just tried Ubuntu 6.10 and have a ton of problems"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by boga on 2007-02-19
Hi, everyone!
I've decided to try Ubuntu 6.10 (i386 Live CD) and encountered a bunch of problems with it:
1. First try in Virtual PC (192Mb RAM, it emulates S3 864 video): Live CD boots but it seems that video mode is incorrect. The image is very distorted (though visible), if I change video resolution to 640x480 it looks slightly better but still unusable
2. My second PC: Duron, KT133A m/b, 256Mb RAM, GeForce2 MX, 3C900 LAN adapter, 4Gb Quantum IDE drive. Live CD starts to boot, the brown desktop appears then an error message box saying something like fail to load Gnome appears and is blanked almost instantly (thus I can't reproduce exactly what it was saying). The system hangs.
3. My main PC: Athlon 64, nForce 3 250 m/b, 512Mb RAM, ATI 9200, 3C900 LAN adapter (BNC connection), Cheetah 15K3 18Gb on Tekram 390F. Live CD boots without a problem but I can't set up the network interface (fixed IP). I've checked ifconfig, everything seems to be alright and match my working settings  but ping even of local hosts fails. But this is not the weirdest problem. If I configure DNS (which it can't access since interface doesn't work) all the programs take a lot of time, something like 30 seconds to start. This means that it tries to access the network every time a program is started. In case DNS is not configured it fails instantly and proceeds starting the program and if DNS is configured it spends this time trying to access DNS server. Even microsoft and apple haven't gone that far. :-\
Also when I tried to install it on the hard disk of the main PC (the partition layout was: Primary OS/2 boot manager, Primary FAT16, Primary HPFS, 2.5Gb free space, Logical JFS) it damaged the partition tables so that JFS became inaccessible and I spent a couple of hours fixing partition tables manually.
So the main questions I have so far are:
1. How can I set up TCP/IP? As far as I understand enabling the interface, setting it to fixed IP and setting IP/netmask should be enough to at least ping the local hosts. I've done it correctly, checked it by ifconfig but it still doesn't work.
2. Can I do something about accessing the network each time a program is started? This is going to cause a certain slowdown not saying about the case the network is down and after all I completely dislike the idea of software accessing the network without my request.
3. Can I install it on the partitions created by 3rd party utilities (e.g. DFSEE)  because it fails to create partitions correctly by itself?

---

### Post by EdThaSlayer on 2007-02-19
> 2. Can I do something about accessing the network each time a program is started? This is going to cause a certain slowdown not saying about the case the network is down and after all I completely dislike the idea of software accessing the network without my request.

It depends on what software, your browser would need to acces the network. To counter this I guess you could either edit some settings of that program or install a firewall and block every port and then unblock the ports you need. Personally I use firestarter which you should be able to find in the synaptic package manager. 

> 
Also when I tried to install it on the hard disk of the main PC (the partition layout was: Primary OS/2 boot manager, Primary FAT16, Primary HPFS, 2.5Gb free space, Logical JFS) it damaged the partition tables so that JFS became inaccessible and I spent a couple of hours fixing partition tables manually.

Isn't that a bit too little space for a whole operating system?
I thought that Ubuntu needed 4 gb, your hard drive is too small and too old I guess, maybe another Linux distribution may work on that, or you can try Xubuntu(hopefully it uses less space but I know that it can run fast on old hardware).

---

### Post by jvc26 on 2007-02-19
To run Ubuntu fine I'd consider at least 4Gb if not more like approaching 8-10 if you're planning to use it to any extent. Also you need a swap partition (rough guide 1.5-2x RAM) so you're going to need a bit more space than just the 2.5 GB you're trying with. - DSL/Puppy would be perfectly at home with little footprint, but for Ubuntu you will need a bit more space.
Il

---

### Post by boga on 2007-02-19
> **EdThaSlayer said:**
> It depends on what software, your browser would need to acces the network. 
Yes, the browser does need it. But I can't see why does e.g. calculator or minesweeper need it as well.

About the partition size: it seems to be enough to install Ubuntu, the installation creates around 150Mb swap partition and the rest is used for EXT3 partition and it seems to be enough even something around 500Mb is left free. Of course this is not enough to really use the system but I'm going to provide it more space if it proves to be useful (unfortunately so far it doesn't). Anyway I don't think the reason for either of the problems is insufficient disk space.

So far some updates:
1. The /var/log/messages shows something like:
ADDRCONV (NETDEV_UP): eth1: link is not ready
for 3c900 card/
2. The problem with partition tables is that it creates out of order extended partitions, that is the first extended partition for the last (physically) partition (really the one that existed before) which links to an extended partition record for partition that is physically situated before that partition.

---

### Post by sank on 2007-02-19
> 1. First try in Virtual PC (192Mb RAM, it emulates S3 864 video): Live CD boots but it seems that video mode is incorrect. The image is very distorted (though visible), if I change video resolution to 640x480 it looks slightly better but still unusable

can anybody address this issue?  Would appreciate, thanks.

---

### Post by sank on 2007-02-19
ah HA, I can address that issue:

[http://www.ubuntuforums.org/showthread.php?p=2181163#post2181163](http://www.ubuntuforums.org/showthread.php?p=2181163#post2181163)

---

### Post by boga on 2007-02-20
So far I've found a solution to some of the problems:
1. The 3c900 driver has a kind of problem preventing it working in auto media detect mode. One has to use DOS configuration utility supplied with the card to set it explicitly for BNC. Then it works fine
2. The supplied partitioning software has a problem that produces incompatible partition tables when the logical partitions being created are situated between existing partitions. I've used a 3rd party partitioning software to create partitions then installed to just created partitions.

Still haven't found out why does it try to access the network each time a program is started (this causes a real slowdown if DNS server is unreachable). Is there any utility to track the network access to find out what it tries to access?

---

