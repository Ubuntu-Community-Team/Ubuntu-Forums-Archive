---
title: "Grub location"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by wildsrv on 2006-12-16
Hey I have 4 SATA drives, an IDE, and an Optical. Windows is on my IDE and Linux is on one of my SATA's. My question is how to i find out exactly where GRUB is at. I know it has to read the MBR off my IDE but then it also reads one of my other drives. Please help. I'll see if i can pull up a map of my partitions to help (its kinda complicated to explain).

EDIT:
[Partition Info]("http://i78.photobucket.com/albums/j116/wildsrv/part.jpg")

---

### Post by confused57 on 2006-12-16
It's probable that grub was installed to your IDE drive mbr.
If you can boot to Ubuntu(or use the live cd), open a terminal(Applications--Accessories--Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

The above will list your partitions.

```
cat /boot/grub/menu.lst
```
will list your OS boot entries in grub

```
cat /boot/grub/device.map
```
will list how grub recognizes the order of your hard drives.

You wouldn't be able to use the live cd, without mounting, for the last 2 commands, but you could in an installed Ubuntu...from the live cd, you'd need to mount the Ubuntu partition:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by wildsrv on 2006-12-16
I can boot fine in linux let me reboot back in to linux from windows and see. I guess I forgot some information. I'm trying to set up two of my drives in a RAID 0. And the 2 i've selected don't have any thing on them but it gives me a an ERROR 22 when i try to load/boot. Again there shouldn't be windows or linux on the two so i am kina confused. Will post what i find a a few.

---

### Post by wildsrv on 2006-12-16
OK here is what is listed.

Fdisk -l
```
nathan@nathan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25939   208354986   83  Linux
/dev/sdb2           25940       30401    35841015    f  W95 Ext'd (LBA)
/dev/sdb5           25940       29891    31744408+  83  Linux
/dev/sdb6           29892       30401     4096543+   b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      484516   244196032+   7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24059   193253886    7  HPFS/NTFS
/dev/hda2           24060       24321     2104515    f  W95 Ext'd (LBA)
/dev/hda5           24060       24321     2104483+  82  Linux swap / Solaris
nathan@nathan-desktop:~$           
```

cat /boot/grub/menu.lst

```
nathan@nathan-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/sdb5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/sdb5 ro single
initrd          /boot/initrd.img-2.6.15-27-k7
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb5 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb5 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd2,4)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

nathan@nathan-desktop:~$    
```

and cat /boot/grub/device.map

```
nathan@nathan-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
(hd4)   /dev/sdd
nathan@nathan-desktop:~$          
```

HD0 and HD2(sdb) are where windows and linux are installed. I'm trying to make SDC and SDD RAID 0 but when i pull them out I get Error 22? ideas???

---

### Post by confused57 on 2006-12-16
I'm not familiar with raid configurations, but here's an explanation of grub error 22:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors)

You might want to do a forum and/or google search for raid configurations in Linux.

Everything looks normal in all the outputs of your system that you posted, except your hda didn't show your NTFS partition(which I assume you didn't quite copy all of the fdisk results).

This site has some excellent info on grub, but I'm not sure if anything can help you for your situation:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Sorry I can't help you more, but I'm sure there's someone in the forums that is experienced with a setup similar to yours.  If I understand correctly, just removing the 2 hard drives(sdc & sdd) gives you the error 22 when you try to boot...not necessarily having them configured in a raid 0 setup?

Add:  I just considered another possibility, if just disconnecting the 2 drives gives you the error 22...you might need to go into bios and disable the sdc & sdd SATA controllers to get your system to boot with the drives disconnected...just a thought.

---

### Post by wildsrv on 2006-12-16
You are correct in that just disconnecting them gives me the error. It shouldn't matter if they are connected or not for GRUB or any other OS for that matter as there is nothing on them. I'm assuming a portion of GRUB or for some reason GRUB is looking at them. As youve see from my outputs I'm very confused because they say nothing about SDC/SDD at all. My thought is that if I were able to install grub again with them not connected i would be good. Have it point to SDB and HDA and I should't have any problems. In theory... My concern is that some thing will go crazy and have to play games to get it back to booting. I'm wandering if a portion of GRUB is on HDA and then some more of it is some where else. Or if while installing linux it decided to put GRUB on a different drive for some reason. Is there a way to view the MBR's of all the drives. I don't know i'm just brain storming. Thanks.

---

### Post by confused57 on 2006-12-17
You might want to send Herman, a member of this forum & developer of the hermanzone website, a PM giving him a link to this thread...he's the most knowledgable person concerning bootloaders  I know of,  that may be able to explain what's going on with your system.
He's a really nice person and willing to help us beginners...he'll more than likely see this thread before he reads his PM's.

---

### Post by gn2 on 2006-12-17
If you set up your dual-boot with all those 4 hard drives connected, and used the standard "Live CD" installer, to add Ubuntu to a Windows system, Grub will be on the Windows drive.

---

### Post by wildsrv on 2006-12-17
Thanks. I'll send him a pm. It's just very wierd to me. I'm also gonna play some and see if I can figure out some more.

---

### Post by Herman on 2006-12-18
Hello there wildsrv,
My first suggestion would to get yourself a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") (if you don't already have one), and use Grub's Command Line to investigate a computer.....(Click this link)........[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")

You should find all the hints and tips in that link about how to find out how Grub sees your drives. When SCSI (or Sata), and IDE drives are both present in the same computer, Grub doesn't number the drives the same way as hard disk partitioners like fdisk do. Usually, Grub considers a SATA disk to be number1, even if disk partitioners consider it to be the last disk.
I would guess that with yours, your number1 IDE disk will be considered as number5 by Grub. making your no.2 disk be number1 now according to grub. No3 will be 2, no.4 will be 3 as far as Grub is concerned, and 5 is 4 to grub.... so Grub will probably be installed in number 2 MBR, because that's the one Grub thinks is number1.... But I'm only guessing. :D

> Hey I have 4 SATA drives, an IDE, and an Optical. Windows is on my IDE and Linux is on one of my SATA's. My question is how to i find out exactly where GRUB is at. I know it has to read the MBR off my IDE but then it also reads one of my other drives. Please help.You can boot the MBR of any hard disk if you want to find out which hard disk grub has installed to by pressing either your F8 or F12 key as your computer is booting up for a list of bootable devices and then select a device to boot. That should be the simplest way to find out which disk's MBR contains Grub. (To borrow a trick from gn2) :D

You can also try  chainloading  any hard disk's mbr with commands at Grub's command line interface. ```
root (hd1)
``````
chainloader +1
``````
boot
``` (I hope those a correct, I'm just working from memory here, and it has been a while since I was playing with that particular idea). You can do the same with (hd0,2,3 and 4 if you like, until you find one with Grub in it.

When you boot Ubuntu, you will probably need to edit the menu.lst file with whatever information it thinks is correct, not what the disk partitioner and you think is correct, to get grub to boot your operating systems properly. In other words yuou might have to use 'trial and error'. It would probably be simple if you had either IDE disks only, or Sata disks only.
> I can boot fine in linux let me reboot back in to linux from windows and see. I guess I forgot some information. I'm trying to set up two of my drives in a RAID 0. And the 2 i've selected don't have any thing on them but it gives me a an ERROR 22 when i try to load/boot. Again there shouldn't be windows or linux on the two so i am kina confused. Will post what i find a a few. I don't know anything about RAID 0, I have never tried it myself, so I might not be as much help as I'd like to be. 

I hope that helps a little bit anyway,
Regards, Herman  :D

---

### Post by wildsrv on 2006-12-21
Thanks for your reply and sorry for the delay i've been busy with work ](*,)  But I've looked and this is my out put.
```
grub> find /boot/grub/stage1
 (hd2,4)

grub>   
```

I have found the command and I think i understand that if i type "setup (HD0)" this would install an additonal copy of grub on my first hard drive which i hope/want to be my HDA1. But that is also where windows is. I can put it on SDB where my Root and /home is but it doesn't matter to me. I'm just worried that i don't want to do setup on hd0 if that will over wright my windows and botch that up. Ideas (becides making back up or making boot disk)? Thanks all. :mrgreen:

---

### Post by Herman on 2006-12-21
> I'm just worried that i don't want to do setup on hd0 if that will over wright my windows and botch that up. Ideas (becides making back up or making boot disk)?Hello wildsrv,
My suggestion, which *should* work, is to use grub's 'geometry' command.
You can use grub's geometry command from a grub shell like you're probably using or from Grub's command line. The following link contains an example of how to use grub's geometry command to list your disks and find out which disks are which in grub's opinion, [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

I don't yet own a computer with as many hard disks as yours, or with any Sata disks. I would like to, just so I would be able to try out some experiments in it and learn more about this subject.
The best I can do is explain how my computer's Grub sees my hard disk with and without a usbdisk attached. A usbdisk is classed as an SCSI disk. As far as I know, an SCSI disk causes the same type of behavior in the way Grub detects disks as mixing Sata and IDE disks would.

I have a computer with two IDE disks, hda and hdb.
hda has Windows XP and three Ubuntu installs and a DSL install.
hdb has Windows 98SE and one Ubuntu install and a large data partition.
Normally, hda is called (hd0) by Grub, and hdb is seen as (hd1).
When I boot the computer up with the usbdisk plugged in, the usbdisk becomes (hd0), hda becomes (hd1), and hdb becomes (hd2).

Here is the way I approached a similar problem when I added Grub to my usbdisk. Please read the following link, paying attention to where I explain the use of the geometry command in that example,
 How to add Grub to your USB thumb drive....................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.")

Does that help you?  Can you apply the same method to your situation? 
Regards, Herman :D

---

### Post by wildsrv on 2006-12-21
Thanks,

Your post did help me and assist me in understanding ALOT. However, I'm still running in to some issues. Here is what i have found out. I used the geometry with all my drives. Made note of the partitions and was able to find out what drive was what. I then decided that i was going to "setup (hd2,4)" where my root is. I even tested it and unplugged the 2 drives I'm going to put in an array and had no errors. I then went to the bios and set the 2 for RAID 0 and booted and got error 22. I'm wandering if its changing the numbering on them or some thing. I mean this is the only thing i could think of right now with my limited knowledge of this program. I'm very puzzled if there is any outputs you would like me to post just let me know and again thank you so much for your assistance.:KS

---

### Post by Herman on 2006-12-21
Hmmm. :-k
I imagine setting up RAID will probably will be changing the numbering. Unfortunately, I have no experience with RAID, so I can"t help there.

"setup (hd2,4)" would have installed Grub to the third partition of your second hard disk. I don't see what you would have accomplished by that, although it is a good thing to do. That would be fine if you are going to 'chainload' an operating system in your third hard disk from a Grub or other bootmanager installed somewhere, but the BIOS won't be able to find your partition's bootsector by itself.
The IPL (Initial Program Loader) for Grub or some other bootloader needs to be in at least one of your hard disk's MBR for the BIOS to find it, or in a floppy disk or usbdisk or CD-ROM. You can then chainload the partition from one of those devices.

If you install Grub's IPL to any MBR, (hd1), (hd2), or (hd3) etc, you should be able to configure booting from that disk in CMOS (BIOS), or press your F8 or F12 key while your computer is booting for a menu and select a non-first disk to boot from.

Why don't you just make a '[dd' backup]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd") of the IPL for Windows in your first hard disk's MBR and then install Grub to all your other disk's MBRs. It's sort of a 'scattergun' solution. If you do make a mistake and accidentally overwrite the IPL for Windows you can just restore it again with the other 'dd' command. It will still be the original MBR that you would be restore as opposed to a generic MBR from the FIXMBR command. I can't see how that would do any harm. The MBR is made from the same material as the rest of the hard disk. It can be written to as many times as we like. I haven't worn out any of mine yet, and I change bootloaders quite frequently, as often as I feel like. You do need to be extra careful when using 'dd' commands though.
I am not recommending you actually install Grub to MBR in your first hard disk on purpose because I know you don't want that.  I'm just suggesting making  a backup of it in case of any mistake possibly occurring. That might free you to be a little more adventurous. You can still adventure as cautiously as you like, but you do need to be able to make at least a few calculated risks probably, if you are going to get anything done in a reasonable timespan.

Regards, Herman :D

---

### Post by wildsrv on 2006-12-21
> you should be able to configure booting from that disk in CMOS (BIOS), or press your F8 or F12 key while your computer is booting for a menu and select a non-first disk to boot from.

Its funny you mentioned that as i did chage the settings from which harddrive the bios sees and boots off of first and that fixed my main issue. I'm not trying to edit the menu.lst and update the new settings.
I didn't care if i installed grub in my first harddrive i was worried about it messing up windows. I think by changing the boot order in the bios i was able to fix my issue. As i said before i'm now editing my menu.lst and making sure every thing is working fine. I can boot windows and linux alike its just getting the settings correct. Is there a different way i should arrange my partions and what not for better performance or any thing. I know its working now and there is the saying that "if it aint broke, don't fix it" but that only applys to me some times LOL. Thanks so much Herman you have been great. I'll post back in a few with more information.

---

