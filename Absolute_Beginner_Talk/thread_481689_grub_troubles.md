---
title: "grub troubles"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Bubbo on 2007-06-22
After trying ubuntu on an old hard drive for a week with no major trouble, i've decided to install it on my main hard drives. However, after installation, it won't boot, and grub gives error 17, which i've found out to be that grub doesn't recognise the filesystem.

I'm trying to install it to a 150GB SATA drive (sdc2), with a separate 100MB boot partition(sdc1), a swap partition (sdc3) and a home partition on another 150GB SATA drive (sdb).
I've reinstalled a few times, repartitioned, tried ext3, and reiserfs as filesystems, tried using grub from a floppy, all to no avail. I can see nothing wrong with my menu.lst file.

Please help, this is driving me crazy, and I really don't want to go back to using windows.

---

### Post by confused57 on 2007-06-22
You might want to boot the live cd and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

You could also mount your boot  partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Post the output of your menu.lst and device.map.  For example, if your /boot is mounted in the directory /media/ubuntu:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```


Hopefully this will give a clue as to what's going on...for your menu.lst, just post your OS boot entries.
Please don't post it as a Notepad .txt file...the formatting just isn't there & it's hard to decipher.

---

### Post by logos34 on 2007-06-22
According to your menu.lst, it's pointing to your /boot partition at '(hd3,0)', menaing the fourth hard disk in your computer (seems you only have three, which means it's counting your cdrom as one.  I saw an example of this just recently).  Grub starts counting at 0 (hd0, hd1, hd2 etc).  I don't think this is a filesystem issue.  Ext3 should work just fine.

Grub is probably just confused by the change in the bios boot order (when you installed maybe it was different than what it is now).  So you're getting the grub menu but it just hangs at error 17.  You can try this:

boot to grub menu, hit 'e' on the top highlighed kernel, and edit the 'root' line.  Instead of (hd3,0), try 0,1,2 in place of the 3.  Hit 'enter' after each change and 'b' to boot.  One of them should work.  Make the change permanent when you boot into linux by editing menu.lst. Open a terminal and type:

gksudo gedit /path/to/boot/grub/menu.lst

and change all instances of (hd3,0) accordingly.

---

### Post by logos34 on 2007-06-22
soory confused57, I was typing away oblivious that you had already posted.

---

### Post by confused57 on 2007-06-22
> **logos34 said:**
> soory confused57, I was typing away oblivious that you had already posted.

No problem, a little assistance is always appreciated.  I've found that with grub error 17, some people don't even get the grub boot menu, which leads me to believe it might be a bios hard drive setting:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

the Super Grub Disk might be a good idea for the OP to try, also.

---

### Post by logos34 on 2007-06-22
> I've found that with grub error 17, some people don't even get the grub boot menu

perhaps not, I guess I had some other recent case in mind where the guy was getting the menu, but error 17 after choosing the kernel.  All these grub errors are beginning to run together in my mind, i think!

---

### Post by confused57 on 2007-06-22
> **logos34 said:**
> perhaps not, I guess I had some other recent case in mind where the guy was getting the menu, but error 17 after choosing the kernel.  All these grub errors are beginning to run together in my mind, i think!
Your advice was "right-on", but I was thinking there was the possibility that he was getting the error 17 and no boot menu.

---

