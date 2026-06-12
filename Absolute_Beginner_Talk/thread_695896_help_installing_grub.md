---
title: "help installing grub"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by erdinnaya on 2008-02-13
i have 2 hard disks. C has windows on it. D is formatted and free. I tried to install ubuntu 7.10 to D. i have downloaded iso file and created image cd. it is a live cd and i installed ubuntu from "use safe graphics mode" choice of the main menu of the live cd. then i learned that this way it doesnt install grub on mbr. so i was getting "error loading op. system" sign. i was suggested to install using "install to hard disk" choice in the menu of the live cd. but my cd doesnt have that choice in the menu. there are only use/install linux, use linux, use in safe mode, memory test, oem install etc. how can i install grub with this cd?

PS: i want to install grub on hard disk D. not my master hard disk that has windows on it. instead i want it on my slave hard disk.

---

### Post by seventhc on 2008-02-13
If you boot back to the live cd, once it's booted up you will see an icon to install on your desktop.
So insert the cd, let it boot up the normal way and you will see it. :)

---

### Post by erdinnaya on 2008-02-13
look.. i ALREADY installed linux USING that icon on desktop. i learned that it doesnt install grub automatically. how can i install GRUB?

---

### Post by seventhc on 2008-02-13
First. don't cop an attitude.
second:
Booting without the cd, what options do you see?
Do you see any menu or does it go straight to windows?

---

### Post by erdinnaya on 2008-02-13
ok sorry for that.

booting without cd i get "error loading operating system" on blank black  monitor. i am almost sure the installation wizard or whatever didnt installed grub on mbr.

---

### Post by erdinnaya on 2008-02-13
PS: i installed it on hard disk D. so nothing to do with windows. i choose to boot from my other hard disk pressing F8 on asus bios screen.

---

### Post by seventhc on 2008-02-13
OK, so you go into the BIOS to change boot priority and when you choose the ubuntu partition your getting an error?
If that is the case it should just boot into ubuntu as it would be acting as it's own drive, and it should have installed grub.
If your in windows do you see the D: drive? If so how much space is being used. Grub would have been installed if you installed ubuntu.
I've installed Ubuntu on a few computers, and grub has always been installed.
Although I'm not sure if safe graphics mode would effect anything, I sort of doubt that would matter.
Unless I'm missing something here and sorry if I am.

---

### Post by erdinnaya on 2008-02-13
i chose the linux hard disk in bios yes (reminder: 2 separate hard disks insted of two partitions on single one) and get the error. Its good you asked i forgot ;in windows explorer i cant see D: it is as if i only have C:. in disk management utility in windows, i can see D: as in two partitions. One partition (72 GB) is in fact not unallocated but doesnt have a drive letter (like F: etc.) and other partition (3 GB or so) is marked as "logical drive" And all these partitions seem to have 99% free space. (As i didnt magnetically formatted the disk before, just quick-formatted) I had to use "safe graphics mode" because i firstly tried to installed from "run/install" section but the installation process had stuck in 15%. Then i learned this wouldnt happen in that safe mode. And now i also heard that by installing, using the "install" desktop icon on linux it wouldnt install GRUB automatically (in my case neither manually). Is it true? A second question: i am told that the installation process should ask me if i wanted to install grub at the end of copying files. i wasnt asked that question during my process why is that?

---

### Post by seventhc on 2008-02-13
I don't think I've ever been asked if it wants to install grub with Ubuntu. It just does it.
I am confused though, who told you it wouldn't install grub? It always has for me, and Ubuntu should also format your drive as ext3 and you should also have a swap drive.

I don't think windows can see ext3 so it shouldn't show up in windows, but it might show up under disk manager. It's been so long since I've used windows I'm not to sure.
During the install did you choose manual or guided?
I think you should boot to the live cd and open do 1 of 2 things
either:
open a terminal and put
```
gksudo gparted
```
post a screen shot or just tell us what you see.

or open a terminal andpost the output of this
```
sudo fdisk -l
```then we can see what partitions you have on the drive where ubuntu is supposed to be.

---

### Post by erdinnaya on 2008-02-14
Today i installed it again not guided manually. i created 10GB ext3 and 2GB swap partition. The install process completed with no problems. But at "advanced" screen during installation, it said "install boot loader to: (hd0)" what is hd0? is it the hard disk i choose to install? Or is is my master hard disk which has windows on it? It seems grub is installed to neither of them. This time when i boot from my linux-installed hard disk, i get blank black screen with nothing. and when i boot from my master hard disk, i get windows xp as usual (without asking me operating system selection, just loads windows).

errr.. about screeen shots. :):confused: how i am supposed to send screen shots in linux live cd?

---

### Post by StGeorge on 2008-02-14
See 
[http://ubuntuforums.org/showthread.php?t=24113&page=17](http://ubuntuforums.org/showthread.php?t=24113&page=17)
The second hard drive is called hd1.
If your ubuntu is at the beginning of the drive it is called (hd1,1).
Re install and look for the advanced tab right at the end.

---

### Post by SteveHillier on 2008-02-14
> **erdinnaya said:**
> 
errr.. about screeen shots. :):confused: how i am supposed to send screen shots in linux live cd?
When I have to do similar with openSUSE from a live CD i simply emailed the stuff out to one of my other email addresses.  So you could do your screen shot.  Save it to your home folder and then send it as an attachment.  Even I was surprised when I did it!!

---

### Post by antoz on 2008-02-14
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

The above link offers all the information you would ever need about grub, I have used instructions from this site before to reinstall grub after reinstalling Windows which removes  it.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

This is another good site for information about Ubuntu, hope this helps. A.

---

