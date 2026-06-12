---
title: "Ubuntu Duel Boot ( 2 Drives )"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-10
Hi, I'm thinking of doing a Duel Boot on my Windows Machine and have a few questions.
Currently I'm running Windows XP Professional and Ubuntu 7.04 in VirtualBox.
What I'd like to do is Run Ubuntu Natively so I can get the True Speed out
of the OS.

So, here's my layout.....

40 Gig Parallel Drive ( OS Drive )  --- Master
60 Gig Parallel Drive  ( BackUp Drive ) ---  Slave
80 Gig SATA Drive  ( Blank )

What I'd like to do is use the entire SATA Drive for Ubuntu
I'd set up a Root, Swap, and Home Partition on this Drive.

Also, I use Ghost to Image my OS Drive onto DVD's
With this kinda Setup how would that affect my current
OS Backup. Since the Boot loader would be different,
what would happen if I didn't Image the Linux Drive?

Could someone tell me If I can do this and list the steps.
I've never tried to Boot 2 different OS's from 2 different drives.
Also one will be on IDE 1 and the other on a SATA connection.
This sounds tricky to me.

---

### Post by dpar on 2007-10-10
> Sometimes people have two physically separate hard drives. You should treat that the same as having two pre-defined partitions. The same principles apply. You can have one hard drive be Windows, the other be Ubuntu. You can partition the first drive to be Windows and Ubuntu and then make the second drive a place to store shared data.

This is from this page....[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by SpiritIsReality on 2007-10-10
by god it's a bit tricky you say, but very dooable. but check out everything I tell you just to be sure you know what you are doing is right, I may be wrong.

search sata and pata hard drives in the same box when trying to install ubuntu. grub has a problem of telling what's going on when they're mixed, but there's lots of answers of how to get it done.

what was the question again? gotta check
ok check out the hermanzone site,
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
 and I'd recommend using the alternate install cd. 
your partitioning seems like it'd work ok. but the more you know about partitioning the better you can handle your rig. for example, when you want to reinstall, and use a seperate home partition shared by many os's you can end up in some difficulty.
everybody has an idea of how to backup, and if you've got a good backup ? ... I mean to reinstall you could have a lot of your settings saved if you( back up) have a separate /etc
and /usr for each os you install.

I like having a small 10GB for each os, then a /data partition and a  max 5GB /fat32 partition
for swapping dvd's between os's like wxp and linux.
if you have a separate /etc /usr /var /home /you know, then it's going to take some time to set up, I mean learniing how to set up. I think a separate all the partitions for each os, each having about 10GB total or 15GB, then a /data partition taking the rest of the disk.
10GB for every os you want to install a lot of stuff on, like kubuntu-desktop on top of a regular ubuntu install. That's what I'm doing right now. 
10G  ext3 Ubuntu
10G ext3 Etch
10G FreeBSD
1g Debian Etch minimal install to run the grub at mbr (hd0)
2times the size of ram or max to 2G  swap
oh, once you get to partition #4 make it an extended partition then the rest of the partitions you want to make, make them in there,
[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)
tx

---

### Post by Orbital75 on 2007-10-10
Good Article but It doesn't mention anything thing about
Using SATA and Parallel Drive in a Duel Boot Situation.

Also, I'd like to hear something address my Ghost issue.

Thanks for the info though..... :)

Great site with loads of good reading.

---

### Post by kshane on 2007-10-10
> **Orbital75 said:**
> Good Article but It doesn't mention anything thing about
Using SATA and Parallel Drive in a Duel Boot Situation.

Also, I'd like to hear something address my Ghost issue.

Thanks for the info though..... :)

Great site with loads of good reading.

Your drives should show up as HDA, HDB and SDA (SDA being the drive to install to)...  Treat them as though they were partitions...

Kevin

---

### Post by Orbital75 on 2007-10-10
Ah, I see.... I understand the Labeling now..... 
HDA ( Hard Drive Master )  HDB ( Hard Drive Slave )--- SDA ( Serial Drive Master )

Thanks.....

Any idea about the Ghost and the Boot Loader.
If I use Windows to Ghost my C and D partitions
on my 40 Gig drive the Boot Loader will contain 
Linux information. So if for some reason I take
that SATA drive out would my windows not boot?  :confused:

---

### Post by maybeway36 on 2007-10-10
If you took the SATA drive out, and that had GRUB (Ubuntu bootloader) on it, then I guess your computer would then try the parallel drives. So Windows should still boot even if you took it out.

---

