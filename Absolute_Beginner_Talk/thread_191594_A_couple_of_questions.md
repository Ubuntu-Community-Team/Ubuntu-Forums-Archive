---
title: "A couple of questions"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by razorblade416 on 2006-06-07
Hi, I'm new to anything but Windows, and I am very willing to learn about Linux as well as very bored this summer. This seems like a good place to start my learning, until I found the minimal system requirements.....

I currently am running a 400mhz AMD K6, 128MB RAM, 8MB video card (1024X768), and a 40GB HDD (only 8GB partitioned off for Linux though), and I am running Windows 98SE. I saw that you can use an alternate installation for computers that have less than 192MB of RAM, but I am starting to wonder if this will always be a problem. Will my computer be able to function properly using Ubuntu? Or will my specs always be in the way?

Next question, my computer cannot boot to a CD. Can you start the Live CD in DOS? Or do you offer any boot floppys to run the CD?

Finally, can Ubuntu run on a FAT32 partition? If not, can my HDD have more than one type of partition at a time?

Sorry for the bombardment of questions, Thanks in advance!

---

### Post by u.b.u.n.t.u on 2006-06-07
Hi razorblade416,

As far as I know...

* ubuntu can run on about the same hardware specs as 98SE.

* ubuntu needs a CD to install or an internet or LAN connection. DOS = FAT16 and unbuntu can in theory run on that. I don't know if the Live CD can boot from DOS, I suspect it should - the CD has some type of autoexec bat file you will need to initiate.

* 128 RAM would be the minimum for a normal install. Just take it easy on the multitasking.

* Yes unbuntu can run on FAT32. Ext3 is better (no defraging of data).

* Yes you can have multiple partitions. (The order of install is important, Windows first).

---

### Post by razorblade416 on 2006-06-07
Thanks for the response. I guess I can always try out how fast it runs on the Live CD. No harm in testing if the CD works. 

One last question though. Does the Live CD affect the Master Boot Record? Or can I just pop in the CD whenever I want to use it without it changing my computer? If it does change it, or if I chose to keep Ubuntu, can I put GRUB on a boot floppy so that it only asks me if I want to boot Linux when I put in the floppy? Sorry, I've had some bad expirences changing anything labled "Master" or "BIOS" ;)

---

### Post by confused57 on 2006-06-07
[QUOTE=razorblade416]Thanks for the response. I guess I can always try out how fast it runs on the Live CD. No harm in testing if the CD works. 

One last question though. Does the Live CD affect the Master Boot Record? Or can I just pop in the CD whenever I want to use it without it changing my computer? If it does change it, or if I chose to keep Ubuntu, can I put GRUB on a boot floppy so that it only asks me if I want to boot Linux when I put in the floppy? Sorry, I've had some bad expirences changing anything labled "Master" or "BIOS" ;)[/QUOTE]

You can use a Smart Boot Floppy to enable booting from CD(for older pc's that cannot boot from CD):
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

Here's some options for installing Grub, using the alternate cd:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

Your 128 mb of ram will be your biggest limitation to using the LiveCD, you can try it...it will be slow, but at least you'll know if your hardware is compatible with Ubuntu, the LiveCD does not affect your computer system(just runs from ram).  If it is then use the alternate iso to install with.  The installer will reformat the partition to ext3, which is better than fat32 for Linux

You might want to consider Xubuntu, it's a lighter distro & may run faster on your system...my old computer is 500 Mhz with 256 ram & it runs pretty fast, firefox is a tad slow.
You'll probably get plenty of other ideas from other posters, but this should get you started formulating a "plan".

Read the dualboot guides:

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by sameerkale on 2006-06-07
I just had the same problem yesterday about booting from the CD. What you do is restart, and when the computer starts to boot, hit F2. You get the BIOS-something screen. You have to change the "boot order" to where the computer boots from the CD drive first, before the hard disk. Whammo.

---

### Post by razorblade416 on 2006-06-07
[QUOTE=sameerkale]I just had the same problem yesterday about booting from the CD. What you do is restart, and when the computer starts to boot, hit F2. You get the BIOS-something screen. You have to change the "boot order" to where the computer boots from the CD drive first, before the hard disk. Whammo.[/QUOTE]

My computer dosen't have that option. When my computer was made CD Drives were optional! :D 

But thanks for the links guys. I'm glad Grub dosn't have to affect the MBR and there is a floppy to make the boot to CD work. 

Question: Is xUbuntu still GUI? And is it still supported? I really want the computer to be fast but I don't want to give up ALL the eye candy. ;)

---

### Post by confused57 on 2006-06-07
Yes it's supported just like Dapper(it's XubuntuDapper6.06):
[http://www.ubuntu.com/ubuntu/philosophy](http://www.ubuntu.com/ubuntu/philosophy)

---

