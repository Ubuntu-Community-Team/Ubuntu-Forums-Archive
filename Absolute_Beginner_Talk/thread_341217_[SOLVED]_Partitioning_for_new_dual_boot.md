---
title: "[SOLVED] Partitioning for new dual boot"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-01-18
I have two hard drives, a 20 and a 160, and I want to put xp on the 20 and Ubuntu on the 160. How many partitions will Ubuntu need? Is it three, one for files and one for swap? And, how big do they need to be? I would like to use a couple of partitions for other things.

---

### Post by jayteebee on 2007-01-18
Hi, I have just done a dual boot install With windows (bleh!) XP and Ubuntu 6.06.
It was really straight forward.

You can manually set the partition information for linux you'll need for example a swap partition to double your memeory and the rest as / .

I installed win xp first then installed ubuntu without any problems so far.

---

### Post by ieee488 on 2007-01-18
Install Windows XP first.
If you are wanting to use XP, 20GB may not be enough.
So, install it in 20GB and format the 120GB to FAT32.

Then when you install Ubuntu, leave part of the 120GB for Windows XP to use and which you can use to share files with Ubuntu.
Then create the /  and  swap partitions for Ubuntu. It will want to take the entire disk so you'll need to change it.

It sounds much more complicated than it is, but pay attention at that part of the install.

---

### Post by rusty4r on 2007-01-18
sharing a partition with xp sounds good for files. What is the / ? and how much for it and you said it will want to take up the rest so how do i avoid that?

---

### Post by bodhi.zazen on 2007-01-18
Ubuntu root = 20 Gb
Swap = RAM X 2, [/b]MAX 1 Gb[/b]

Rest fat or ext3 for data sharing

You can use this to access ext3 from windows :

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Install XP first

Then Ubuntu

Put Grub into the MBR :)

---

### Post by ieee488 on 2007-01-18
The  /   is basically for the entire Ubuntu OS.

As I recall, you'll basically have to choose the menu choice of Manually Edit Partition Table if you don't want Ubuntu to take up the entire 2nd hard drive.

Even if you get it wrong, it's not the end of the world because you can download gParted, burn the ISO to a CD and go in afterwards to shrink Ubuntu.

---

### Post by jvc26 on 2007-01-18
/ is the root for the filesystem. In linux all the files are arranged on a tree with / being the main trunk, so to speak. From / all the drives and folders are accessible for instance /home/$username$ playing a similar role to my documents in windows. /mnt/hdc1 for instance may be the mount point of a hard drive labeled hdc1. For ubuntu, I would recommend putting it on 3 partitions. My reasoning for this is as follows:
1/ Have this partition for your / (i.e. the root of the whole filesystem)
2/ Secondly have a separate partition for /home. This is because then you can reinstall / without having to mess up all your settings and the like.
3/ This partition acts as the swap space for the ubuntu OS. This as a rule should correspond in size to 2x your RAM (as I see bodhi mentioned above)
:) Hope that helps,
Il

---

### Post by rusty4r on 2007-01-18
Thanks, I'll try 20 for the root 1 for the swap and about 40 for files. Are the other programs such as office and image software installed in the same partition as the root or in the files part?

---

### Post by jvc26 on 2007-01-18
Applications will be installed to the root part. Your files part, mounted as /home contains settings for apps in hidden files and all your documents, music whatever other stuff you want to put in there.
Il

---

### Post by rusty4r on 2007-01-18
so maybe i should make the root 30 or 40 because i like to tinker with apps

---

### Post by bodhi.zazen on 2007-01-18
Size of root 20-40 Gb will not matter so much. Linux apps are not that large. 

Data, however, is different ....

---

### Post by rusty4r on 2007-01-20
thanks guys i got it done worked just fine and i am a proud new dual booter :)

---

### Post by bodhi.zazen on 2007-01-20
Welcome in from the cold ;)

---

### Post by Anderssj on 2007-01-21
Hey I noticed you guys have mentioned installing windows first in most of these replies. Ive installed ubuntu to a fresh drive and now i want to install windows server 2003 to a separate, secondary,  partition. However it seems windows is not recognizing the file format ubuntu converted my drive to. What program should I use to remedy this?

---

### Post by bodhi.zazen on 2007-01-21
After you install windows you will need to restore grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Then use this to access ext2 and ext3. If you used another file system for Ubuntu, as far as I know, you are SOL (Short on Luck).

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

