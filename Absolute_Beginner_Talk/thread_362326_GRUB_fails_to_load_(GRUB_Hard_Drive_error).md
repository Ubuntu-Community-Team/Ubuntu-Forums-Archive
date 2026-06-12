---
title: "GRUB fails to load (GRUB Hard Drive error)"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by NeonShadow on 2007-02-15
I've posted this in another section, but this is probably a more appropriate place for the issue.

Yesterday, I installed Ubuntu 6.10 on my freshly repaired laptop (Qosmio F15-AV201 was fixed by toshiba on a mainboard recall - oddly enough, not it has SATA hard drive and nVidia GeForce Go 6600 instead of PATA drive and GeForce FX Go 5700)....

When I boot up, BIOS loads and then GRUB throws error: "GRUB hard disk error"

If I reboot with live CD and choose last option (to boot from first hard drive), grub GUI comes up and I am able to choose Linux kernell or boot into windoze (both work fine btw, and all new partitions seem to be ok)...

Grub device.map file has following in it: (hd0) /dev/sda
It looks like a correct setting, since I only have one hard drive with 4 partitions, which get mounted as sda1 (NTSF), sda2 (swap), sda3 (ext3) and sda4 (FAT32)

In my last post I was told to check BIOS settings :confused: , but haven't the slightest on how to do that (sorry mostly a noob here), but if someone could direct me to the right place, I'd be more then happy to learn :D

I really want to get this stuff working again - been waiting over a month for toshiba to send it back to me and have some projects that need to be put on this machine... please help!

---

### Post by Sbarton on 2007-02-15
Hi!, To get to your BIOS you need to generally tap 'Delete' or 'F8' on bootup. I would suggest you have a look at the Motherboard manual to know what the settings should be. If you do not know your MBoard you should find that via the system information. You can do a Google to find out the MBoard and also the manual to find the settings.
HTH
regards

---

### Post by bjornolai on 2007-02-15
I'm quite a knob myself, but if it's a problem with the grub you might find the super grub disk usefull. It has functions for restoring your grub or even making a new one. 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by NeonShadow on 2007-02-16
so I went through BIOS and still can't find anything wrong....

Haven't ran the super grub disk yet, but in the mean time - any more suggestions?

The issue is 100% with grub, because I can boot using the live CD and choosing to boot from hard drive - grub GUI starts up and windows and ubuntu load fine (posting this from ubuntu right now).

Any more advice is greatly appreciated!

---

### Post by bodhi.zazen on 2007-02-16
Which grub error (number) ?

Second, boot the the live CD

post the output of : ```
sudo fdisk -l
```

also post menu.lst :

```
sudo mkdir /media/ubuntu
sudo mount /dev/xxx /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

Note:
/dev/xxx is your ubuntu partition ( ? /dev/hda2 or /dev/hda1 or /dev/sda1 ??)

that is a small "L" in menu.lst and not the number 1

---

### Post by NeonShadow on 2007-02-16
Error has no number, just reads "GRUB Hard disk error"


fdisk -l

```

Disk /dev/sda: 79.9 GB, 79925045760 bytes
255 heads, 63 sectors/track, 9717 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            9457        9717     2096482+  82  Linux swap / Solaris
/dev/sda3            2612        8150    44492017+   b  W95 FAT32
/dev/sda4            8151        9456    10490445   83  Linux

```

menu.lst

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9babcb4e-824d-4a13-847e-2e84eb0ff6c7 ro
# kopt_2_6=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

and in case you want it, device.map
```

(hd0)	/dev/sda

```

I've checked everything I could think of.... now I just boot into my HDD using liveCD and the last option on the menu. :confused:

---

### Post by bodhi.zazen on 2007-02-16
Everything looks OK to me.

Hard to know the problem without a more specific grub error.

Perhaps re-install grub to the MBR.

From the live CD, open a terminal

```
sudo grub
```

At the grub prompt :

```
root (hd0,3)
setup (hd0)
quit
```

Re-boot from the HD ...

HTH

---

### Post by arieltammam on 2007-02-16
I’m having the same problem – I think its related to USB support during ubuntu startup.
unfortunately haven't found a solution yet.

---

### Post by bodhi.zazen on 2007-02-16
> **arieltammam said:**
> I’m having the same problem – I think its related to USB support during ubuntu startup.
unfortunately haven't found a solution yet.

SATA drives are sdxy

USB drives are also sdxy

booting to a USB device is related to BIOS.

---

### Post by NeonShadow on 2007-02-17
ok so if SATA drives are sdxy and USB drives are sdxy..... so am I permenantly screwed?

---

### Post by bodhi.zazen on 2007-02-17
> **NeonShadow said:**
> ok so if SATA drives are sdxy and USB drives are sdxy..... so am I permenantly screwed?

LOL NeonShadow

The first disk will be sda

The second will be sdb

The first partition on the first disk will be sda1
[indent]in grub speak that translates to (hd0,0)[/indent]

So no you are not "permenantly screwed", we just need to configure grub :)

Did you try re-installing grub ?

---

### Post by confused57 on 2007-02-17
Here's someone else with a similar problem, read the replies by Herman:
[http://www.ubuntuforums.org/showthread.php?t=363355](http://www.ubuntuforums.org/showthread.php?t=363355)

---

### Post by NeonShadow on 2007-02-18
Thanks for support! And sorry for noobish comment....

Anyhow, I've tried several time to reinstall grub using the liveCD, both times received messages that everything was configured successfully, but every time I have rebooted received exact same error. :confused: 

Person in post above tried super grub disk to no avail... so I guess that's not the answer either.

I've been able to use the laptop booting to live CD and then choosing to boot from hard drive, and everything else functions normally... still kinda confused as to what might be the issue with Grub.

---

### Post by bodhi.zazen on 2007-02-18
From some of the links is the other thread posted by confused57 it may be a bios problem.

Try updating your bios ...

---

### Post by NeonShadow on 2007-02-18
Just tried updating the BIOS... first downloaded manufacturer installed for windows (booted in XP) - it showed me as having the latest version.... So I decided to run updates provided with laptop when toshiba returned the computer with new mainboard. No luck either.

So basically, I'm out of ideas yet again... :confused: 

Unless I'm doing something wrong as far as BIOS update.

---

### Post by NeonShadow on 2007-02-18
anyone?

---

### Post by Patrick K on 2007-02-18
Sorry, I don't have any help to offer. Here is a forum that is for grub problems, maybe they might have an answer:
[http://www.nabble.com/Grub-f1675.html](http://www.nabble.com/Grub-f1675.html)

---

### Post by NeonShadow on 2007-02-19
Well, so far everything I find points me to grub/BIOS conflict, but I can't seem to find any BIOS updates for my laptop - everything says BIOS is up to date.... :confused: 

Any more input is greatly appreciated!

---

### Post by Sbarton on 2007-02-19
Hi!, NeonShadow. So did _YOU! _try the SuperGrubDisk to reinstall grub.I have used it on a number of occasions and it did what it says. Of course that does'nt mean it will in all circumstances, but it's worth a try. In the end would it be a disaster to try reinstalling Ubuntu?
Just for your info I had a few bugs with 'EDGY' and reinstalled 'DAPPER' It seems to be more stable.
regards

---

### Post by NeonShadow on 2007-02-19
will try the super grub disk tonight (ran out of empty CDs)....

I have reinstalled edgy 4 times now.... laptop has no important data on it, so I was actually contemplating formating the hard drive and reinstalling windoze... then repartitioning it again and so on...

This is my second laptop - more powerful of the two, so it acts as my toy.

Reason I want to keep it dual-boot is that there some apps that I need that will not run on Linux and have no viable alternatives.

---

### Post by Sbarton on 2007-02-20
I know what you mean about keeping 'Windows' for some apllications, I do so myself. Although I only had 'EDGY' installed for a short while, the only benefit for me was the quicker boot loading and shutdown, no big deal though, it's only seconds. If you don't have any luck with SuperGrub disk reconsider 'Dapper' it will be supported for longer than 'Edgy'

---

### Post by NeonShadow on 2007-02-20
I'm fairly confident that this issue has nothing to do with Ubuntu itself - it's running like a champ!

The problem seems to be with GRUB itself.

---

### Post by Sbarton on 2007-02-20
Well, if you find the answer please post back. I'm sure others will find it worthwhile.
regards

---

### Post by HeoU on 2007-04-20
I've a Qosmio F10, and when I install Ubuntu 7.04, I get exactly same error like NeonShadow.

So anyone else have idea to fix it?

@ NeonShadow : Did you get an answer?

Thanks

HeoU

---

### Post by HeoU on 2007-04-21
Is there somebody can help me?

HeoU

---

### Post by MoGa on 2007-05-10
[COLOR="Purple"]I get the same messege and u know .. i have Qosmio E15 and Windows MCE like you ,, so i think there is some thing error with Toshiba LT's and i hope some one find a solution for this problem, i tired 2 use the CD each time i want to use my LT, please help.


Thank u.

MoGa[/COLOR]

---

### Post by Shazaam on 2007-05-10
Has anyone tried to change the hardrive boot order in bios yet? Such as changing it from hd0 to hd1? Or sd0 to sd1 if its listed?
BTW I have tried the Super Grub Disk but it seemed to have a problem recognising the way my Soyo KT600 mb treats SATA hardrives so I get the HARD DRIVE ERROR notice when I try to run it.

---

### Post by Evan_G on 2007-05-14
I'm having the same  problem.  My motherboard is a GA-7N400 PRO 2.  I've had problems before, so I tried to install LILO instead.  Here is what I ran into:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; LILO configuration. &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                                                                                                        &#9474;  
 &#9474; WARNING!                                                                                                                                               &#9474;  
 &#9474;                                                                                                                                                        &#9474;  
 &#9474; Your /etc/fstab configuration file gives device UUID=b954c1e1-bea2-4d65-bd89-023c5343a52b as the root filesystem device. This doesn't look to me like  &#9474;  
 &#9474; an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple      &#9474;  
 &#9474; configuration program does not handle.                                                                                                                 &#9474;  
 &#9474;                                                                                                                                                        &#9474;  
 &#9474; You should either repair the situation or hand-roll your own /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig again to retry   &#9474;  
 &#9474; the configuration process. Documentation for LILO can be found in /usr/share/doc/lilo/.         
```

Although my mobo supports Raid, I do not have it set up, and did not have a problem installing Ubuntu 6.06 with GRUB (the last time I did a clean install).

So I looked at the the /etc/fstab file and got:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b954c1e1-bea2-4d65-bd89-023c5343a52b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=71ac843d-453e-4f97-8f1d-cb51445fb793 /home           ext3    defaults        0       2
# /dev/hda1
UUID=8e22b67e-4db5-499e-b55b-47f22d69dd1e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```


Is there a way to install LILO instead of grub from the start?  I don't have anything important on my hard drive at this point, so I don't care about reinstalling from scratch.  Though I would like to find a solution without having to do that again.  I'll try the super grub disc as well.

EDIT: I tried using the Super Grub Disk, but I had not success in re-installing Grub.

---

### Post by psusi on 2007-05-14
What is this about a usb disk?  What kind?  Have you tried unplugging it?

Try what was suggest earlier and reinstall grub, but add the --force-lba option.  Use the cd to boot from the hard disk like you have been then:

sudo grub
root (hd0,3)
setup (hd0) --force-lba


If that doesn't work then I'd suggest reformatting and install with a /boot partition at the start of the disk.  There are some bios issues with booting to partitions above 2 or 8 gigs.

---

### Post by Evan_G on 2007-05-15
I believe this is an issue with Grub and various motherboards.  Unfortunately, the bios for my motherboard can only be updated through Windows, so I am out of luck if that issue can be resolved with that.  I have had problems with grub before, and the only time I have got it to work on my computer was with Ubuntu 6.06.  I remember even as far back when I tried Debian Woody, and it didn't work then either.  I have never had a problem with Lilo.  Is there any way to have it so that it can install Lilo instead of Grub through the graphical installer?  Or will I be forced to get the iso of the text based install?


EDIT:

Just as aside for anyone who might have this problem and stumble upon this thread, a work around on this problem is to install an older version of Ubuntu, and do a dist-upgrade.  Worked for me.

---

### Post by adrian15 on 2007-05-17
> **NeonShadow said:**
> In my last post I was told to check BIOS settings :confused: , but haven't the slightest on how to do that (sorry mostly a noob here), but if someone could direct me to the right place, I'd be more then happy to learn :D

I would go into the bios and check if LBA is on or off and try if then it boots ok.

adrian15

---

### Post by swappa on 2007-07-07
Just  wanted to say that I have the exact same error. 
I have two SATA2 drives and one IDE drive. The first SATA drive is all Vista and the second is all Kubuntu. Now, the strange part is  that this worked perfectly when i had Vista/Ubuntu in a dual boot setup but when I installed Kubuntu (I formated the drive with Ubuntu and installed Kubuntu). The IDE drive is just a backkup drive. Putting the Kubuntu CD in the DVD makes Kubuntu boot. If the CD is not there, it gives me the error. From what I can tell this seems to be  something more than just a 'grub newbie' issue. Hopefully a workaround will come our way soon. ;)

---

### Post by swappa on 2007-07-07
Just  wanted to say that I have the exact same error. 
I have two SATA2 drives and one IDE drive. The first SATA drive is all Vista and the second is all Kubuntu. Now, the strange part is  that this worked perfectly when i had Vista/Ubuntu in a dual boot setup but when I installed Kubuntu (I formated the drive with Ubuntu and installed Kubuntu) things got all wrong. The IDE drive is just a backkup drive. Putting the Kubuntu CD in the DVD makes Kubuntu boot. If the CD is not there, it gives me the error. From what I can tell this seems to be  something more than just a 'grub newbie' issue. Hopefully a workaround will come our way soon. ;)

---

### Post by alex_in_welly on 2007-09-20
ok, i'm a complete noob when it comes to computers but i just love linux and everything about ubuntu. i had the exact same problem when installing 7.04 on my crapped out lap top. not knowing much about what was wrong i tried to work my way around the problem. for me all i had to do was reinstall using the alternative text based disk and that did the trick. i hope it may work for you too.

---

### Post by aas452 on 2007-11-11
Now I tried to download ubuntu on my second drive and a new error came up

Error loading operating system

I am going to wipe the drive and start over again this time loading ubuntu on the first disk

---

