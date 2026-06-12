---
title: "Bual-Booting Ubuntu+Windows98"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by PhosPhoton on 2007-07-15
I was in a bit of a rush... after I installed Ubuntu I decided to partition my hard drive and install Windows 98 as well. I was successful in that, but now I don't know how to boot back into Ubuntu. All I get is a blank screen... :-(

---

### Post by oilchangeguy on 2007-07-15
> **PhosPhoton said:**
> I was in a bit of a rush... after I installed Ubuntu I decided to partition my hard drive and install Windows 98 as well. I was successful in that, but now I don't know how to boot back into Ubuntu. All I get is a blank screen... :-(

you should install windows first. it overwrote grub. you can get it back by using the live cd, and reinstall it.

---

### Post by ajgreeny on 2007-07-15
Have a look at the following txt file which should help you out.  This assumes you can still boot into windows, of course.

---

### Post by PhosPhoton on 2007-07-15
thanks ajgreeny it worked. But now I have more trouble. Ubuntu has hung on the loading screen, the orange bar almost filled up, and my computer is just stuck there doing absolutely nothing, not even making a noise.

EDIT: Now grub is spitting out a lot of bad error messages that don't look to good :-(
 It says "-bash: /dev/null Permission Denied"
And I can no longer boot into Windows... this seems a bit pointless...

---

### Post by PhosPhoton on 2007-07-16
bump

---

### Post by ajgreeny on 2007-07-17
I think you may have changed your partition nomenclature by reinstalling windows, though I don't see how that would let you get to the stage you have.

Anyway, try booting into the ubuntu liveCD, and then in a terminal type
sudo fdisk -l
This will show you all the hard disk partitions you have.  Now mount your ubuntu partition with 
sudo mkdir /media/ubuntu
This will make a folder to mount ubuntu to.  Now
sudo mount /dev/hdxX /media/ubuntu/ -t ext3  (the hdxX is the partition shown in fdisk -l as your ubuntu one, perhaps hda2)
This will do the mounting.  You can now navigate with nautilus to the file system place you need to check the /boot/grub/menu.lst and if needed you can edit it with gedit.  If you need to add an entry for windows add the following to the bottom of the list:-

title        Microsoft Windows 98
root        (hd0,0)
savedefault
makeactive
chainloader    +1

I hope this helps, but if you need to come back again and we'll see what we can do.

---

### Post by PhosPhoton on 2007-07-17
Its doing the same thing still...

my fdisk said Linux is on /dev/hda1 and windows is on /dev/hda3 and my swap partition is on /dev/hda5

and find /boot/grub/stage1 gave me (hd0,1)

and I can't seem to find /boot/grub, its not even there :confused:

---

### Post by oilchangeguy on 2007-07-17
i suggest formating the hard drive and starting fresh. install windows first. then install ubuntu, and let it set the partitions itself. no manual partitioning.

---

### Post by ajgreeny on 2007-07-17
I'm afraid I agree with oilchangeguy, as it sounds as though you've managed to completely bork the system(s) on your machine and this seems the quickest and easiest way forward.  > and I can't seem to find /boot/grub, its not even there
Actually it is there;  your command **find /boot/grub/stage1** did find it on (hd0,1)

 So now as he says:-
1  Reformat the whole drive and install windows on it, using the whole drive.  Once that is up and running:-
2  Install Ubuntu on the same drive by shrinking the windows partition using gparted on the live install CD to the size you want and then using the unallocated space for Ubuntu.  Let the installer do its own from this point, don't worry about separate /home, or the size of your swap, just go for the default install.  Put grub on the windows mbr and then you can chose at boot time which to use.

Good luck!

---

### Post by PhosPhoton on 2007-07-19
Well I guess that sounds like my only option... I'm getting used to it now, I've screwed up Ubuntu 3 times already (this'll be my fourth) and had to format each time... the only problem is now I'm going to lose a few files that may have had some value, but it's too late now... they weren't *that* important i guess :)

I appreciate all your help :popcorn:

---

### Post by ajgreeny on 2007-07-19
Ifv you now have your windows install working you could copy the important files to that partition using explore2fs which you've already looked at - as long as you have not done the formatting already.

---

### Post by PhosPhoton on 2007-07-20
No its fine, they weren't that important really, just stuff that was backed up, stuff I could easily redo, and other things I got from the internet. thanks anyway

Everything works perfectly now after formatting the entire hard drive and installing windows first and then ubuntu.

---

