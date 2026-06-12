---
title: "GRUB won't load after installing windows"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by LiNoah on 2007-01-08
This is my first post on this board, thanks to the helpful community around here, i've been able to overcome every single problem i encountered so far by searching these forums.

I've tried searching for an answer to my problem but couldn't find what to do, only what i should have done, wich as i understand is install windows first and linux second. A few weeks ago i tried ubuntu for the first time, using dapper drake as my first linux encounter. I soon fell in love with the fresh experience and decided to swith to ubuntu as my main os, cleansing both my hard drives and starting the edgy live CD.

First i deleted all the partitions to start from scratch. I intented to use one harddrive (primary master, hda) to run my os from, and my second drive (primary slave, sda) for storage. I also intended to make a partioning scheme that could get along for a while to prevent me from reinstalling and repartitioning as i learn more about this OS.

so this is how i did my partitioning, in right order:

80 GB IDE (hda) :
hda1: 100 MB /boot
left another 100 MB or so blank # without having any clue as to why, but that just "felt good". Is there any sense in leaving some space in between partitions?
hda2: 20 GB  /
left blank the remaining 60 GB.

200 GB ATA (sda):
1.5 GB swap    
remaining GB /home

Then i continued to install Edgy 64bit on my AMD X2, wich worked like a charm. All was well. Until this evening, when i decided to to reinstall windows XP, mainly for gaming and some DRM'd bestiality. I added a 20 GB FAT32 partition at the end of hda with gpart, and converted that to NTFS with the windows installer. Then i installed windows xp pro.

Now, and as i know now to be expected, booting my computer gets me straight into windows, skipping GRUB in total. Windows has overwritten my MBR.
So my question is, **How do i get GRUB reinstalled?**

It would be cool if i could do this from the bootmenu on the live cd, since booting ubuntu from this one takes me another 20 minutes staring at some i/o error wich keeps repeating until it finally starts loading the desktop etc. ("Huh? expected null handler" or smt like that)


Thanks in advance for any help or comment on what i did that you can give me.

---

### Post by Tomosaur on 2007-01-08
windows overwrites the MBR. You need to reinstall GRUB from the LiveCD. There is a howto on the forum somewhere, search for 'how to reinstall GRUB'.

---

### Post by LiNoah on 2007-01-08
Great, thanks for the quick reply.

Using the right words for a search (I should have figured that one out ), and i easily found this link [http://www.ubuntuforums.org/showthread.php?t=224351]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=how+to+reinstall+GRUB")

Thanks again for the effort of helping us newbs.

---

### Post by Tomosaur on 2007-01-08
No problem, that's why we're here :)

---

### Post by ajmorris on 2007-01-08
to re-install grub load the livecd. Then open a command line and mount your linux partition with write permissions.[PHP]sudo mount -w "partition" (make sure you in /media)[/PHP]

Then do[PHP]sudo grub[/PHP]

then in the grub console type [PHP]root (hd"hard disk number",partition number (known from when you mounted you linux partition) [/PHP]

then type [PHP]setup (hd0)[/PHP]

Note: if that was confusing here is what i do when i mount mine

[PHP]cd /media
sudo mount -w hda6
sudo grub
root (hd0,**5**) 
set (hd0)[/PHP]

The reason why (hd0,**5**) is in bold is because the partition number in linux is started from 0. So my hard disk number is 6 so when i mount my partition it is hda6 but when i use (hd0,5) it is 5. 

Hope that wasn't too confusing.

---

### Post by ajmorris on 2007-01-08
sorry for my last post. I was posting when you posted your reply.


Lol

---

### Post by harmeet on 2007-01-08
Here is one post that talks about it -

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by LiNoah on 2007-01-08
Hehe thanks a lot anyway, it is usefull since it saves me from booting ubuntu, and with that another dull 20 minutes of waiting.

I'll give it a go.

---

### Post by LiNoah on 2007-01-08
Lol and harmeet thanks to you as well.

I'm sort of getting overwhelmed with all this quick help i get from here. I hope one day i can return the favor to a new generation of linux newbies.

Again, people like you guys are great and keeping a great linux experience *from* turn*ing* into frustration. I guess the name ubuntu is ultimately suitable!

---

