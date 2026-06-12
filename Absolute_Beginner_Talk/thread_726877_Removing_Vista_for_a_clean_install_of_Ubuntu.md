---
title: "Removing Vista for a clean install of Ubuntu"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by BluesDrive on 2008-03-17
I'm having problems creating a partition, so I'm in the process of relocating the system files and pagefile so that I can create a partition.  However, I'd like to get rid of Vista altogether so I can run Ubuntu as my main and only OS.  I've only used Ubuntu once before, and that was a dual-boot laptop with XP.  I was wondering if there was some sort of way to get rid of vista altogether and just have a clean install of Ubuntu.

If it helps any, I'm running Vista home premium 32-bit on a Sony VGN-AR 570.  I'd also like to know if I'll have to do some sort of edit for the built in wireless internet/bluetooth function and the volume control/media shortcut buttons.  I don't really care much for the built-in webcam, but if I could get it to work, that'd be awesome.

I'm tired of my laptop running slower than a clogged toilet when I paid $2000...all because of the OS.  I have no problem learning something completely new [if I were to buy one of those dummy books or something of the sort, do I buy the debian(sp?) for Ubuntu?].

Also, if anybody has any experience with blackberrys and Ubuntu, could you share that experience with me?  I'm a heavy blackberry user currently on the 8320.  I'd just like to know whether you got the desktop manager running, etc etc.


Thanks in advance for all and any help.  If anymore info is needed, feel free to PM or e-mail me.  I'll respond as soon as I'm able to.

---

### Post by NightwishFan on 2008-03-17
If you wish to remove Vista use the "use entire disk" option in the Ubuntu installer. Back up data you want first. Remember this will utterly delete that umm virus I mean OS known as Windows. Make sure your ready for that. Hardware in Ubuntu can be of mixed functionality, however keys on my keyboard for suspend work on Ubuntu and not in windows so...

---

### Post by BluesDrive on 2008-03-17
and I won't need to re-format the main drive/partition to FAT32 or the other one? (g3ps?)  Thanks for your super speed, btw.

---

### Post by NightwishFan on 2008-03-17
The option to use entire disk will be on the specified disk, clean it of all data and install Ubuntu to a ext3 filesystem and will set up a swap partition.

---

### Post by jan quark on 2008-03-17
linux ubuntu uses the ext3 partition type

if you choose "use whole disk" during the partition process during the installation ubuntu will automatically format it to ext3

and ask before you act :)

read here for more info
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Ub1476 on 2008-03-17
When installing Ubuntu, you can choose to 
1: Install Ubuntu on HDD 
2: Resize HDD and install Ubuntu
3: Use free space available (if you already have made a partition)
4: Manual

Wireless can be an issue with Linux, but usually it works fine. If there's no Linux driver available, ndiswrapper can install a Windows wifi driver. If your computer is brand new, the next Ubuntu will be released in April which will have the latest kernel (which has much better driver support than the current Ubuntu uses).

I don't have any experience with bluetooth nor blackberry..

Websites and this forum should provide you with all your questions. I don't see any need for a book.

---

### Post by BluesDrive on 2008-03-17
Sweet.  I'm gonna go try this now.  I'll tell you if it works or if it doesn't.

---

### Post by BluesDrive on 2008-03-17
It's giving me this error
/bin/sh: can't access tty; job control turned off

---

### Post by jayg1169 on 2008-03-17
If nobody helps with the error. you could try downloading DBAN and burning it to disc. it will totally wipe the drive (does take a while)

---

### Post by NightwishFan on 2008-03-17
When are you getting this error.

---

### Post by Ub1476 on 2008-03-17
[Read through this thread (especially the last page)]("http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page4.html")

---

### Post by BluesDrive on 2008-03-17
I've tried every solution in that last page, none worked so far.  Most of the problems and solutions come from desktop users and involve unplugging floppy drives and optical drives.  I can't do that.

EDIT:  This error that keeps happening happens just a little bit after I being installation or whatever it is.  I don't even really start installing anything.  Should I try to use a lower version instead of gibbon?

---

### Post by mab1376 on 2008-04-01
im trying to install ubuntu 7.10 over my vista partition but the vista bootloader keeps overriding grub from my xp partition since thats the primary partition, how can i remove it without formatting?

fixboot and fixmbr from the recovery console do not work btw.

---

