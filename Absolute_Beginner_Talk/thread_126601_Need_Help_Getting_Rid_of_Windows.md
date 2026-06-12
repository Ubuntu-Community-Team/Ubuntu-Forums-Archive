---
title: "Need Help Getting Rid of Windows"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Mr X on 2006-02-06
I wish to install ubuntu on my computer. How do I instal ubuntu and then get rid of Windows XP?

---

### Post by Mr X on 2006-02-06
Anybody? I just wanna remove windows.

---

### Post by Ulysses on 2006-02-06
I am frighteningly new at this so take my advice with a grain of salt
#1
Get the CD. 
You can download it if you are smart. I couldn't manage it. But you probably can. I ordered it through the ubuntu homepage. It took a few weeks but that was okay.
#2
If you ordered the CD, the time you spend waiting can be spent backing up everything you hold near and dear to your heart. Pictures. Music. Documents. Email. The whole kit and kaboodle.
If you downloaded the CD, still do this.
Do not pass over this. Getting rid of windows means that ubuntu wipes it out. Kills it good.
#3
Install the software
Do not partition (I didn't / go big or go home, I say). Just give 'er. Think about it. The worst case scenario is that if it doesn't work, you get your hands on a windows install CD (not all that hard) and reinstall windows on your system.
Ubuntu is the easiest and the smoothest of the operating systems. The other one would be Slackware (so I'm told / I haven't tried it), You will not have a problem.
#4
BE CAREFUL with the hardware you buy
Yeah, I went out and bought a cheap printer and it turns out that ubuntu doesn't have a driver for it. But I'm patient. Another good thing about ubuntu - you are now active in your system, more than just pointing and clicking your way obliviously.

This is my advice, for what it's worth. And I have less than 2 weeks experience.

RAR

---

### Post by Hygelac on 2006-02-06
If so, when you go to install K/Ubuntu you can reformat your entire hardrive for it, which is an effective way to remove Windows (although this would be before, not after, the installation of K/Ubuntu).

EDIT: Oh, someone beat me too it lol.

---

### Post by devnulljp on 2006-02-06
Boot from the install CD and tell it to use the entire drive. That will remove your windows partition. You can partition or not for Linux, up to you. A separate /home partition means you can replace or update the entire system without losing your files.

If you've already installed Ubuntu as double boot and want to get rid of windows, you can try either fdisk from the cli or gpartedit, wipe out the windows partition. Use gpartedit to resize your working ubuntu partition to fill the drive.

---

### Post by towsonu2003 on 2006-02-07
here's my 2 turkish liras ;)

1. Don't get rid of Windows just yet... Instead, do a dual boot system so that when you are stuck in Linux, you can boot to Windows and get help. I've been using Linux for a couple of months and I still need Windows from time to time (hardware issues; go online if networks goes hoink; play games; tweak word documents that won't open in OpenOffice; get hardware info; boot to Windows when I call a computer consumer support line like my ISP -so they won't say "ooohhh we don't suport linuxxxx" etc etc)

2. Download the LiveCD and give it a try. See if your hardware works nicely in Ubuntu, and solve problems (take notes at least) before installing: so you'll know what to expect after the first installed boot.

3. If you like the LiveCD, ***backup all your data*** and do a dual boot install. For dual boot, you may need to resize your ntfs partition, create a new (or two, one for / and one for /home) partition with a linux native patition, and also a fat32 partiton (small) as a file transfering gateway btw Windows and Linux. 

Good luck :)

PS. Some reading about partitioning: [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

---

