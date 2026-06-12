---
title: "New Laptop - need suggestions"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by antihero on 2006-12-27
Hey everyone. 

I just purchased a Dell Inspiron e1405 laptop.

Intel Core 2 Duo Processor T5600 (2MB/1.83GHz/667MHz)
14.1 Inch TrueLife Wide-screenWXGA+
1GB Shared Dual Channel DDR2 SDRAM 533MHZ
Intel PRO/Wireless 3945 802.11a/g Mini Card

I'm going to attempt to dual boot XP media center and Ubuntu.  I've done a great deal of research, but I wanted to gather some personalized advice before I attempt my very first Linux installation. 

So, here are my questions:

1. How should I partition my 120 GB HD?  I was thinking: 

25 GB NTFS for XP
10 GB Ext3 for /
2 GB Linux Swap
3 GB FAT32 (just in case)
80 GB Ext3 for /home (shared - I'll be using a 3rd party tool in XP to read/write to this partition)

2. Which version of Ubuntu should I go with: Dapper or Edgy?  Would Edgy be better because my hardware is pretty new?  I like the fact that Dapper is fully supported.

3. Should I use EasyUbuntu?

4. Anything else I should be aware of going in?

Also, if anyone has any links to e1405 specific installation tutorial, that'd be excellent.  I know I'm going to have to do some tweaking to get everything to work properly.

Thanks so much!

-antihero

---

### Post by sgbeamer on 2006-12-27
I started with Warty on my HP Pavilion laptop (18 months old) and have been through 2 upgrades on it with no problems.  I would try the live CD and if most everything works then go with Edgy otherwise, Dapper will work just fine.  Depending on which OS you run more frequently you may want to give XP some additional space since it's a hog.  The only time I find myself using XP is to find network connections in hotels.  Sometimes I have trouble finding them with Ubuntu but it may be that I'm just not using the right tools.

---

### Post by houstonbofh on 2006-12-27
I have traditionally cut the drive in half, and given half to XP, and let Ubuntu autoconfigure the rest.  It usually picks a swap partition much smaller than 2 gig, and a single / partition.  I like single partitions so I don't have to play "guess the freespace location" in the file system.  I do not use FAT32 as the ntfs-3g is quite good. [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by antihero on 2006-12-27
Thanks for the input.

Can anyone comment on the benefits of creating a /home partition in addition to / ?  Also, any opinions on EasyUbuntu?

---

### Post by riven0 on 2006-12-27
As far as EasyUbuntu it's simply a script you download to install all the necessary codecs and graphics drivers. So I don't see anything wrong with it. You can read about it [here]("http://easyubuntu.freecontrib.org/").

---

### Post by GreenMedallion on 2006-12-27
I have a Dell e1405 and had great success installing Ubuntu. I actually installed Dapper AMD 64 off a CD. I downloaded the "alternative" install CD. This gives you the text-based install procedure, and went very smoothly for me. 

There is a great set of instructions I followed for partitioning and the install. Read through this prior to install and then follow each step while installing and it should be OK. (I had two laptops side by side, one to read the site, the other to install on) - [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

You should note there seems to be a common problem toward the end of the install where the screen goes black except for one or two white squares. This is becuase the video settings aren't configured yet. Don't panic if this happens! The install is still finishing it is just in the background. Watch your HD indicator and hit "enter" every five minutes or so. Eventually the CD should pop out and you'll know the install finished.

When you boot back up you may not get the Ubuntu start page. The site I note above mentions this ("But what if you don't get the login screen as most people do, but instead got a message about the X-server and end up with a command prompt on a black background? You might need to use the sudo dpkg-reconfigure xserver-xorg command, here's what to expect") and the site links to-

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

After that even, you will need to install 915resolution to get the correct widescreen resolution running. 

I would suggest Automatix. It is a better solution than EasyUbuntu (which kept having problems for me). Also Swiftfox 32bit worked well as a browser better than Firefox 64bit. The only problem I am still having seems to be a power management issue - can't get the hibernate/suspend to work, and the computer freeze if i plug in the power adapter or vice versa. Otherwise, smooth running ubuntu.

good luck!

---

### Post by houstonbofh on 2006-12-29
> **antihero said:**
> Thanks for the input.

Can anyone comment on the benefits of creating a /home partition in addition to / ?  Also, any opinions on EasyUbuntu?
If you frequently rebuild your system, you can just reformat your / partition, and leave your /home partition alone, and all your files/settings are already there.  /boot can be handy for large filesystems on old BIOSes, but I have only needed it on servers with unsupported out of the box hardware RAID.  Some poeple do /var/log to keep runaway log files from filling up the / system, but again that is usually only needed on a server.

---

### Post by NeoLithium on 2006-12-29
I'd suggest dropping the swap size as well, unless you're running really heavy processes that would require it, I have 512RAM/512Swap and never had a problem yet, even with compiling, movies, music, multiple programs, if you might be worried, maybe 1GB for swap; but the old days of 2x your ram for an idea, is pretty much done; so you can give yourself a bit more usable HD space.

---

### Post by geo_bio on 2006-12-29
With that 120, I will suppose you have 112 gigs since it's usually overstated (120*10^9 is actually only 111.759 gigs if you count a gig as 1024^3 bytes)

I would give windows about 40 gigs, 1 gig for swap, 30 gigs for Ubuntu ext3 /, and the rest (~41 gigs) for /home. I'm assuming that you will be putting all your files into the /home so that it can easily be accessed from both OS's w/o accidentally messing with something in the other OS. And regarding the file sharing, you don't need to use some special software. As long as you save it as a physical partition using NTFS(recommended) or FAT32, you will be able to access it with both OS's.

If you dont mind some problems or errors, go for edgy. It's newer, and should support more, but I know that drapper is quite stable. I've heard of problems in edgy, but also of a lot of new hardware supported. I have a very new sony vaio, and I use drapper (6.06). It works fine, and supports the Intel 945GM  chipset (I believe its the same as yours), and the T2300 Core Duo processor.

---

### Post by antihero on 2006-12-31
> **geo_bio said:**
> And regarding the file sharing, you don't need to use some special software. As long as you save it as a physical partition using NTFS(recommended) or FAT32, you will be able to access it with both OS's.

I thought Linux could read, but not write, to NTFS.  I know FAT32 works both ways but it is less efficient than NTFS and Ext3.

---

### Post by houstonbofh on 2007-01-02
You can read and write quite well now. [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by tsvim on 2007-02-16
/home can't work from a FAT32 partition because of permission issues. So if you have a extra partition for home you'll definitely need some 3rd party app for Windows to access it. (Or you could use my solution: create a link to a FAT32 partition under /home and move your "My Documents in Windows to that new partition)

---

