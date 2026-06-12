---
title: "GRUB Error 17 and other Boot Menu Issues"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by linuxman1 on 2007-04-22
This past week I installed Ubuntu 6.1 on my Desktop Computer and then subsequently upgraded to 7.4 (Fiesty Dawn) when prompted.  No major problems with the initial basic install - only outstanding issue after some great support response for the Ubuntu Community was [B]initializing my network ready Brother MFC-5440CN inkjet printer/copier/scanner/fax unit.  But is not the issue that I am seeking help with.

First an overview of my hardware:
**User built system**:
P4 Case (with original PSU removed
3 system fans + dedicated hard drive and DVD fans.
Antec TruePower 2.0 480W PSU
AMD Athlon64 x2 (AM2) 3500+ (retail ... fan and heatsink)
Gigabyte GA-M55Plus-S3G Motherboard (retail ... on-board Geforce 6100 and Realtec HD Audio)
Geil Ultra DDR2 PC6400 (Dual Channel) ... 2 x 512MB
Hitachi PATA 7200rpm 160GB Hard Drive
Pioneer DVD-WR (x16)
Floppy Drive
Logitech MX-Laser Mouse
Modware PS/2 Keyboard
Magview 17" CRT
Brother HL-2040 LaserJet
Epson Perfection 1260 Flatbed Scanner
Cambridge 5 piece Audio Speaker Set
Brother MFC-5440CN (connected over DSL Broadband)
LAN Home network via 2Wire DSL Modem Router.

Second - History of Disk Partitioning and OS Installs:
I have been a Windows user for many years so system was first configured to run multiple instances of Windows 2000 using Partition Commander:

**PARTITIONS**
3 Primary Partitions containing W2K (SP4)
Par#0 - Main W2K install (bootable)
Par#1 - Basic W2K w/ Imaging Software - stores backup image of "Main"  (bootable)
Par#2 - W2K w/ Oracle 9i Server - for learning and testing DBMS tools

1 Extended Partition ([COLOR="RoyalBlue"]was initially configured as a Primary partition with EXT2 format[/COLOR])
Par#4 - (2 logical partitions) - formatted for Linux OS (EXT2 format used) and a 2GB Swap File

Windows "native" boot-manager was used to multi-boot.

All was well in the world of Window land :
(A) Main W2K was brought up to date after time consuming updates of OS and User applications such as MS Office 2003.
(B) Backup image of Main was created and stored on Par#1
(C) W2K OS w/ updates installed on Par#2 but Oracle Server still to be installed.

**Now decided to test and possibly install Linux (Ubuntu)**
(A) Downloaded image file and created Install CD for Ubuntu 6.1
(B) Tested Live CD - things looked good so decided to install to hard drive.
(C) Linux Installer re-partitioned the Extended Partition to add two additional logical partitions by  splitting the original EXT2 in half.
(D) The target half for the Linux install was further partitioned into 2 logical partitions - main was 13.57GB (formatted to EXT3) and the Swap File was about 690MB.

Although I had wanted to *use the entire Extended Partition for the Linux install*, I did not try to alter the defaults chosen by the installer since I was not sure of the impact.  I *also did not want to replace the original MBR* but again was not sure of how to accomplish this.

After the install was completed, *GRUB was now the boot-manager*.  Although everything didn't go as I had intended,  all the partitions were accessible.  From this point, however, things went mainly down hill.

(1) While trying to familiarize myself with Ubuntu,* I inadvertently added the server version to the boot menu*.  
(2) Shortly thereafter I was prompted to upgrade to Ubuntu 7.4 which I did - all went well but it ran the whole night.  Now several additional entries were appeared in the boot menu and you* now had to "page down" to access the Windows Entries* (not sure why there were 2 of these).
(3) Decided to *free up space on the Extended Partition that not being used by the actual Linux install*.  Since some of the EXT2 partiton was being mysteriously marked as used, I decided not to mess with that until some additional research was done. I figured, however, that it would be save to free up the Swap File partition (2.1GB) that I had originally created using Partition Commander.  **Big mistake**.  *Now on bootup GRUB issues the following message and _hangs_*:

Grub loading stage 1.5
Grub loading, please wait ...
Error 17

Now I can't access anything except through the use of the Live CD which allows me to run Ubuntu 6.1.  At this point my main concern is to be  able to access the Windows Partitons and keep them in tact.  I can always re-install Ubantu if necessary.

Attempts to resolve:

(1) I tried to reformat the freed space as a Swap File again (using Partition Commander) - *no change.  Same error*.

(2) After searching various forums, I tried the command strings:
grub
root (hd0,5)
setup (hd0)
quit
*no change.  Same error*.  Also tried several variations of this command sequence.

(3) Running **GParted** (mentioned in part of a post I had read) I noticed that Ubuntu recognizes all the partitons except the Swap FIle that had previously been deleted.
 /dev/hda1  FAT32  60.00 GB
 /dev/hda2  FAT32  43.01 GB
 /dev/hda3  FAT32  20.00 GB
 /dev/hda4  EXTENDED  30.37 GB
    /dev/hda5  EXT2  13.77 GB
    /dev/hda6  EXT3  13.79 GB
    /dev/hda7  Linux-swap  635.35 MB
   [COLOR="RoyalBlue"] /dev/hda8 unknown  2.2 GB[/COLOR]

**Questions**:
Per a number of the posts that I have read, the error occurs because Grub does recognize one or more of the partitions on the hard drive.
(1) Can the problem be fixed using GParted - reformat **[COLOR="RoyalBlue"]/dev/hda8[/COLOR]** ?
(2)  What is the best approach to freeing up [COLOR="RoyalBlue"]/dev/hda5[/COLOR] for later use by Ubuntu or another OS?
(3) What is the best method for clearing unnecessary entries from the Grub Boot Menu?  *Should I just re-install Ubuntu 7.4 from scratch*?
(4) What is the best (cleanest and simplest ) approach for handling multi-boot?  *Have GRUB replace the MBR* (not sure I like any program actually doing this) *or having GRUB called* (MBR not replaced)?  Does having another Linux Distro impact this decision? 

As always all suggestions are much appreciated.

---

### Post by leibowitz on 2007-04-22
Great story. I read everything from it.

> (1) Can the problem be fixed using GParted - reformat /dev/hda8 ?

I don't know. You have to check your **/boot/grub/menu.lst** file to see if anything point to this partition.

> (2) What is the best approach to freeing up /dev/hda5 for later use by Ubuntu or another OS?

I think it would be to configure all of your partition to point to the UUID of them, and not the /dev/ name (that is in your **/etc/fstab** file on linux only) before moving things around. But anyway, if you intend to make the whole extended area available to linux you would like to have your root linux partition starting at hda5 and finishing at hda6, or even more. But I don't think you can delete hda5 and move hda6 back. But maybe, I don't know exactly if it's possible or not. And the answer to this makes a big difference in the decision.

> (3) What is the best method for clearing unnecessary entries from the Grub Boot Menu? Should I just re-install Ubuntu 7.4 from scratch?

No, Please don't. That's just a bit of **/boot/grub/menu.lst** editing. They are just there because a new kernel can crash your computer, so to be sure that you can start it just add every kernel version with one recovery mode for each. That's huge, I know. But you can edit that without any problem, and even put your Windows boot entry on the top (so you don't use Page down anymore).

> (4) What is the best (cleanest and simplest ) approach for handling multi-boot? Have GRUB replace the MBR (not sure I like any program actually doing this) or having GRUB called (MBR not replaced)? Does having another Linux Distro impact this decision? 

I love Grub, and I would say Grub should be on the MBR or not be installed at all. But I'm a kind of linux fanatic. I can prove this.
```
sudo fdisk -l /dev/hda

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3092    24836458+  83  Linux
/dev/hda2            3093        7673    36796882+  83  Linux
/dev/hda3            7675       14946    58412340    5  Extended
/dev/hda5            7675       11901    33953346   83  Linux
/dev/hda6           11902       12059     1269103+  82  Linux swap / Solaris
/dev/hda7           12060       14946    23189796   83  Linux

```

I'm 100% windows-free. Anyway on another computer I am using Grub with Windows XP and Vista but am starting Linux by default anyway. So you don't want any advice from me on that question.

---

### Post by linuxman1 on 2007-04-22
Thanks.  Being spoiled by the fast and fantastic response I received last time I was beginning to feel rather rejected by not hearing from anyone.  But I see that a great many have encountered this issue for different reasons.  I have also read a number of post that all point to examining the same file, **/boot/grub/menu.lst** and possibly editing it.  Since I am using the Live CD to boot into Ubuntu, how do I access this file on the hard drive?

---

### Post by leibowitz on 2007-04-22
Good question.

You boot with the live-cd. Then try to access your root partition (hda6). If you can't do this with the nautilus file manager, then use the Terminal.

Go to the Applications menu > Accessories > Terminal.

And paste this:

```
sudo mkdir /media/myhda6 && sudo mount /dev/hda6 /media/myhda6
```

This will make your partition available in /media/myhda6

Then you can edit your /boot/grub/menu.lst file from this command:

```
gksudo gedit /media/myhda6/boot/grub/menu.lst
```

Paste it here if you need some help.

---

### Post by linuxman1 on 2007-04-22
Thanks again, leibowitz.  I had to step away for a while to make dinner for the family but I appreciate your quick response.  It maybe a little while before I can devote my full attention to this process but I (God willing) will post sometime later tonight if I get stuck.

---

### Post by linuxman1 on 2007-04-23
Here is a display of the file contents 

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
# kopt=root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

title		Ubuntu, kernel 2.6.20-15-server
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-server
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-server (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-server root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro single
initrd		/boot/initrd.img-2.6.20-15-server

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-server
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-server root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-server
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-server (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-server root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro single
initrd		/boot/initrd.img-2.6.17-11-server

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=f431c0d9-5c90-4118-aa90-b5d02976e51d ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by leibowitz on 2007-04-23
I suppose your partition table is a bit messy. I have re-read your message and have understand that your grub menu isn't displaying at all. So you can't boot any os.

And that's ... kind of blocking isn't it.

Ok so just one thing before I say what to do, you can still boot in Windows with some tricks.

When the error is showing on boot, you can write what is in your config file (because for the moment it can't read it).

That is something like this (you may find something to remove/add)
```

root (hd0,0)
savedefault
makeactive
chainloader +1
boot
```

Anyway, it's not the solution to your problem. The solution is to make GRUB active and working again. 
Please boot with a live-cd again and type this into the Terminal, and paste the result in here. I suspect your partition table not to be in proper order.

```
sudo fdisk -l /dev/hda
```

You should see this message in the ouput: "Partition table entries are not in disk order". [1]

If you see this (please check carefully), then you will need to fix it with fdisk. But that's a dangerous task. I would advice to backup your data (do it from the live-session cd) before doing anything to it, just to be sure.

[COLOR="Red"]Warning:[/COLOR] don't do this unless you get the message posted in [1].
> To fix [the partition table order], you need to type this.
sudo fdisk /dev/hda


Warning: be cautious to what is writed in here. Or you can erase your partitions and lose your data. So please read this and carefuly check if everything is right.

In the fdisk utility, every single character is a command. So please begin with "m" to see all the commands available.

Next you need to enter in the "Advanced mode" so use "x".

Again, type "m" to get all the commands avaible in expert mode.

Then, type "f" to fix the order of your partitions.

Now use "w" to save and quit.

Please output everything in here to see if everything is right.


---

### Post by linuxman1 on 2007-04-23
I think that your analysis is correct.  If memory serves we well, I believe that the when Ubuntu did the install the 2 partitions that were created were assigned as #7 and #8.  And the Swap File Partition previously created using Partition Commander had been assigned as #6.  When I deleted this Swap File Partition then both the Ubuntu main Partition and that of its Swap File were re-assigned to #6 and #7.  My later attempt to correct the problem by adding the partition back did not work because the "new" partition was now assigned #8 not its previous designation of #6.

I know that **fdisk** is not something to "monkey around" with since I have been bitten before - "fooled" it into allowing two different types of partition formats to co-exist where they normally shouldn't.  Worked OK until I needed to free up one of the partitions - the "whole house came tumbling down".   Isn't there a safer way - like recovering the original MBR - even if it means re-installing Ubuntu?  I don't have much invested beyond the initial install (but the Windows stuff would be a royal pain to redo).

---

### Post by linuxman1 on 2007-04-23
As per your request, here is the output of FDISK -L:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7833    62918541    c  W95 FAT32 (LBA)
/dev/hda2            7834       13447    45094455    c  W95 FAT32 (LBA)
/dev/hda3           13448       16058    20972857+   c  W95 FAT32 (LBA)
/dev/hda4           16059       20023    31848862+   f  W95 Ext'd (LBA)
/dev/hda5           16059       17855    14434371   83  Linux
/dev/hda6   *       17856       19655    14458468+  83  Linux
/dev/hda7           19656       19736      650601   82  Linux swap / Solaris
/dev/hda8           19737       20023     2305296   82  Linux swap / Solaris


So does this mean that to correct the problem FDISK will be used to re-number the partition assignment?  Would addition corrections be needed?

---

### Post by leibowitz on 2007-04-23
There's no need to re-order anything, unless you have this message "Partition table entries are not in disk order". And it seems you don't. That's ok.

Now your explanation is rather rational, it will help to recover the system.

What you need to do now.
First step is to go to the **/boot/grub/menu.lst** file and replace each occurance of "**root (hd0,6)**" by "**root (hd0,[COLOR="Red"]5[/COLOR])**"

Next step will need to re-install grub on your hard drive, because it's trying to access your hda7 to find the /boot/grub/menu.lst file. And it's in the hda6.

To do this, I must say I don't remember exactly what I did. So please try this first, and tell me if it's not working.

Start with the live-cd session and go to the Applications menu, Accessories, Terminal. And type the following command.
```
sudo grub-install /dev/hda
```

---

### Post by linuxman1 on 2007-04-24
Made the change to **menu.lst** but attempted grub re-install failed:

ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.

Does this mean that you have to mount the drive ... ***sudo mkdir***... before executing the grub-install command?

---

### Post by leibowitz on 2007-04-24
Yep, you have to mount your drive first.

Try again.

```
sudo mkdir /media/myhda6 && sudo mount /dev/hda6 /media/myhda6
```

Then install GRUB.
```
sudo grub-install --root-directory=/media/myhda6 /dev/hda
```

If the last command did not work, then I have an [COLOR="Red"]alternative[/COLOR]. Don't do this unless you have the same error you get.

The success output from grub-install is something looking weird.
> Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when //boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["//boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map //boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda

So If you have something other than that, try this two commands.
[COLOR="Red"]Don't do this unless grub-install failed[/COLOR]
```

sudo chroot /media/myhda6
sudo grub-install /dev/hda
```

---

### Post by linuxman1 on 2007-04-24
leibowitz, you the man!

Thanks for your patient help and support.  Despite the frustration of not being able to access my main systems for the last few days, I have truly enjoyed the learning experience which has helped me to understand the logic behind some of the processes.  It also helps that there has been much progress since the days of line editors such as EDLIN.  The command-driven process also allowed the user to see what was doing on - great for an old techie like me but I suspect still too much for the average Windows neotype.  Ubuntu 7.4 is quite impressive and getting much closer to an OS that can handle the normal Windows user.  With increasing support from Hardware vendors, one of the biggest "weaknesses" continue to shrink in importance.  Of course, the most attractive feature of Linux is its fabulous community network.  This most precious entity is ultimately what will swing the pendulum but only after a greater lever of user-friendliness has been achieved. 

As for myself, I have seen enough to convince me to commit to becoming an active advocate.  A special thanks again to you and all the other tireless, willing community supporters.   Graphics (default) was also much improved for actions such as scrolling which had been "maddeningly" choppy.

**P.S. **
FYI - Some of your infancies assumed that the Live CD that I was using was Fiesty Dawn but recall that I had upgraded from 6.1.  Yesterday, after resolving a burn issue I was able to use a 7.4 Live CD which resolved and extended quite a few features - Nautilus now showed all the drive partitions (not just the Live CD and USB Flash Drive) and it no longer hung on Restart or Shutdown. 

Not sure if your profile indicated that you had an AMD Athlon64 4600+ system.  If yes, then I may request a bit more advice.

Live Long and Prosper.

---

### Post by leibowitz on 2007-04-25
No prob. 

happy to see your main problem resolved.

---

