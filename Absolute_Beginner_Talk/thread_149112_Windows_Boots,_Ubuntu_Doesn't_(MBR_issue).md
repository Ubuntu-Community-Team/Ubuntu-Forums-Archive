---
title: "Windows Boots, Ubuntu Doesn't (MBR issue)"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by dafinga on 2006-03-23
This is my first try at Linux and I am loving Ubuntu!  So here is the issue ...

I installed Ubuntu on a 10gb partition on a IDE WD 120gb HD.  I was able to boot into Ubuntu and everything was working great.  Though when choosing Windows XP, I wasn't able to boot into Windows. 

Windows is installed on a WD 37.7 SATA Raptor on **SDA**.  So I booted on my Windows install CD into recovery and on the console type FIXMBR.  This was able to fix my issue of getting into Windows, but now I cannot boot into my UBUNTU install.

I went to this [thread]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=windows+bootloader"), but while booting on the Ubuntu LIVE CD, there was no solution.  I would rather have Windows to be the primary OS to boot to, but if its Ubuntu, that will be fine too.  I just need to be able to get into either OS on the fly.

Thanks in advance

---

### Post by Brunellus on 2006-03-23
...but windows as primary OS is no fun!

I believe you can get around the problem by specifying windows first in grub's menu.list file

---

### Post by dermotti on 2006-03-23
Your best bet is returning Grub to the mbr, and researching booting windows from grub. Ubuntu more than likely configured the windows entry wrong. 

Took me about 4 hours of screwed around to finally get my menu.list configured properly so it would boot windows.

---

### Post by dafinga on 2006-03-23
hehehe ... I know its not, but its for RADMIN Purposes for now, until I really figure out Linux.

I cannot even boot to Ubuntu, so changing the menu.list file won't even matter, will it?  I don't even see the GRUB bootloader, to choose what OS to get too.

---

### Post by dafinga on 2006-03-23
To set GRUB as the master MBR ... can I do that in the partition table like when I first installed?

---

### Post by gnu2tux on 2006-03-23
yeah I think the command is grub-install (hd0).

Regards,

Ali

---

### Post by njzillest on 2006-03-23
i had the same problem after you repair your windows partition


boot up your ubuntu installer disk. check the hardware and etc... when you go to the partition stage, click "go back"


it will bring up a list... go to grub, and reinstall your ubutnu to your MBR (try to use that, if it doesnt work then install it to the partiton-- although im not sure what results you should get-- i did installl fedora to my partiton but i had to do a little more for it to work). When you boot your computer, the grub should load with ubuntu.


any problems just PM me or IM me (AIM) at njzillest101

---

### Post by njzillest on 2006-03-23
i forgot to mention.. DO NOT REINSTALL UBUNUTU.. this happend to me and i took me hours to figure it out.



do not reformatt your disk.. the OS is still on your HD!

---

### Post by dafinga on 2006-03-23
[QUOTE=njzillest]i had the same problem after you repair your windows partition


boot up your ubuntu installer disk. check the hardware and etc... when you go to the partition stage, click "go back"


it will bring up a list... go to grub, and reinstall your ubutnu to your MBR (try to use that, if it doesnt work then install it to the partiton-- although im not sure what results you should get-- i did installl fedora to my partiton but i had to do a little more for it to work). When you boot your computer, the grub should load with ubuntu.


any problems just PM me or IM me (AIM) at njzillest101[/QUOTE]

Thanks man ... I will try this.  I will not format as well.

---

### Post by Fatjoint on 2006-03-23
If you have the following things, it can be a lot easier.

1) you have ubuntu live cd
2) you have linux installed and you know what partition it lays upon
3) you have windows installed and you know what partition it lays upon

If you boot the live CD and go to the grub directory you can install GRUB onto whatever partition you want.

The next step is to edit the menu.lst file under /boot/grub and make sure the partitions are set up correctly there.  Here is my menu.lst file:

> 
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd          /initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd          /initrd.img-2.6.12-10-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title          Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


As you can see I have windows installed on the first partition of my drive (hd0,0), and ubuntu installed on the second partition (hd0,1)

The next step you need to do is make sure on your Windows partition that your file boot.ini is configured correctly.  This is windows bootloader file (think the same thing as GRUB).  It needs to be set to the correct partition as well.

> 
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


As you can see above, windows is told that I'm booting from hd0,1.

That's all there is to it.

---

### Post by dafinga on 2006-03-23
OK ... here is the new thing.   Also, thank you all for all the quick and helpful posts ... you guys/gals rock!

When I set the boot order (in bios) to my SATA drive (Windows install), I boot into Windows.  

When I set the boot order (in bios) to my IDE drive (Ubuntu install), Grub comes up and I can choose ONLY my Ubuntu install.

I tried to change my menu.lst and I edited to this:

> 
title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/hda5 ro quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/vmlinuz root=/dev/hda5 ro single
initrd		/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,0)
kernel		/vmlinuz.old root=/dev/hda5 ro quiet splash
initrd		/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,0)
kernel		/vmlinuz.old root=/dev/hda5 ro single
initrd		/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-amd64-generic root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(sd0,0)
savedefault
makeactive
chainloader	+1


I get an error when I choose the Windows XP install in GRUB.  It displays:

> 
Booting 'Microsoft Windows XP Professional'

root (sd0,0)

Error 23: Error while parsing number


I know that the **(sd0,0)** is wrong, but I am not sure what to put there?  I know my partition is set on **sda1**, but how do I put that in the menu.lst file?

---

### Post by dafinga on 2006-03-23
^Bump

---

