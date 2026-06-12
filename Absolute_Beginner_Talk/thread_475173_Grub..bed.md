---
title: "Grub..bed"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by virtualy on 2007-06-15
I just loaded Ubuntu via a downloaded .iso burned to disk.  The installation went fine but I am now unable to boot into my Windows HD.  I can boot to Ubuntu without any problem.  When I select the Windows HD in CMOS (or BIOS, I don't know which) as the primary drive from which to load, I get a Grub error (#21) and the launch fails.

What happened and how do I fix it?

Thanks.

---

### Post by logos34 on 2007-06-15
a little more detail please, 

In ubuntu, open a terminal and type these cmmands:

sudo lshw -C disk

sudo fdisk -l

cat /boot/grub/menu.lst

cat /boot/grub/device.map

cat /etc/fstab

Just copy and post the whole thing.

Isn't there an entry for windows on the grub boot menu?  Windows Vista or XP?  

Grub seems to have installed to the mbr of the drive that you installed ubuntu on...which should have left the windows bootloader on the windows drive untouched.  not sure what the deal is.

---

### Post by virtualy on 2007-06-15
Thanks so much for the reply.  The data requested is below.  I should tell you that I had no intention of installing a boot loader.  I had wanted to select the HD to boot from BIOS, planning to eventually migrate completely to Linux and to use Parallels to launch any MS programs I might still need.  I selected an installation to the SCSI drive but Ubuntu seems to have placed a boot loader (Grub?) on the IDE drive; though it *did* install Ubuntu to the SCSI drive.  ??

IOW, if I completely disconnect the SCSI drive, on which Ubuntu is installed, and try to boot, I get the error as described.  Ditto if I leave the SCSI drive attached and select to boot from the IDE drive in BIOS.

There are no entries for the grub boot menu - indeed, there is no menu at all.

Thinking that may be the problem, I tried to repair the mbr on the ***IDE*** drive via XP install disk, but no joy.

BTW, I can still view the IDE HD, and its contents, from Ubuntu (on the SCSI HD).

Thanks again.

~$ sudo lshw -C disk
Password:
  *-disk                  
       description: SCSI Disk
       product: ST3200822AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 3.01
       serial: 3LJ2AR3Z
       size: 186GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@1:0.0.0,1
          logical name: /dev/sda1
          capacity: 183GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@1:0.0.0,2
          logical name: /dev/sda2
          size: 2957MB
          capacity: 2957MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 2957MB
             capabilities: nofs
  *-disk
       description: ATA Disk
       product: ST3200820A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 3.AAE
       serial: 5QE2GHKE
       size: 186GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
     *-volume
          description: HPFS/NTFS partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 186GB
          capabilities: primary bootable
  *-cdrom:0
       description: DVD writer
       product: PLEXTOR DVDR PX-740A
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.01
       serial: 508084301268
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: LITE-ON CD-RW SOHR-5238S
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: 4S06
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdd
  *-disk:0
       description: SCSI Disk
       product: CardReader CF RW
       vendor: USB2.0
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 0814
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: CardReader Combo
       vendor: USB2.0
       physical id: 0.0.1
       bus info: scsi@2:0.0.1
       logical name: /dev/sdd
       version: 0814
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdd
  *-disk
       description: SCSI Disk
       product: USB2.OFlash Disk
       vendor: CRUCIAL
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 2.00
       size: 247MB
       capabilities: removable
       configuration: ansiversion=2
     *-disc
          physical id: 0
          logical name: /dev/sdb
          size: 247MB
          capabilities: partitioned partitioned:dos
        *-volume
             description: FAT16 partition
             physical id: 1
             logical name: /dev/sdb1
             capacity: 246MB
             capabilities: primary bootable

~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

~$ cat/boot/grub/device.map
bash: cat/boot/grub/device.map: No such file or directory

~$ cat /boot/grub/menu.lst
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
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=50ba664b-250b-407d-8056-2fba07542805 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=50ba664b-250b-407d-8056-2fba07542805 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=50ba664b-250b-407d-8056-2fba07542805 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=50ba664b-250b-407d-8056-2fba07542805 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=50ba664b-250b-407d-8056-2fba07542805 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50ba664b-250b-407d-8056-2fba07542805 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=29a9d549-1450-4016-b90f-a2c7acd74618 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by trak87 on 2007-06-15
With grub you don't need to go into the system bios to select which drive to boot up. That's what grub is for and is probably why it is confused when you change settings in the bios.

It's possible that you overwrote your windows partition when you installed Ubuntu. If you installed correctly, you should not be having a situation where your Windows partition is missing. Ubuntu can detect it and add it to a selection menu upon boot but only if you didn't overwrite it during the Ubuntu install.

---

### Post by trak87 on 2007-06-15
With grub you don't need to go into the system bios to select which drive to boot up. That's what grub is for and is probably why it is confused when you change settings in the bios.

It's possible that you overwrote your windows partition when you installed Ubuntu. If you installed correctly, you should not be having a situation where your Windows partition is missing. During install, Ubuntu can detect the windows partition and add it to a selection menu upon boot but only if you didn't overwrite the Windows partition it during the Ubuntu install.

---

### Post by virtualy on 2007-06-15
I understand what grub is for (I think).  For my purposes, it is unneeded and not wanted - which is why I never intended for it to be installed.

I did *not* overwrite my Windows partition (thank the fates).  In fact, there is no "partition" - just two separate HDs with an OS on each, Linux and XP.

Thanks.

---

### Post by confused57 on 2007-06-15
> **virtualy said:**
> I understand what grub is for (I think).  For my purposes, it is unneeded and not wanted - which is why I never intended for it to be installed.

I did *not* overwrite my Windows partition (thank the fates).  In fact, there is no "partition" - just two separate HDs with an OS on each, Linux and XP.

Thanks.
It won't affect your system, but you might try adding an entry to boot Windows from grub:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

add it to the very end of your menu.lst

```
sudo fdisk -l
```
the -l is a lowercase "L"

Evidently, you also have grub installed to your Windows hard drive's mbr since you're getting a grub error by booting first to your Window's drive.

---

### Post by Skidpad on 2007-06-15
> **virtualy said:**
> I understand what grub is for (I think).  For my purposes, it is unneeded and not wanted - which is why I never intended for it to be installed.

I did *not* overwrite my Windows partition (thank the fates).  In fact, there is no "partition" - just two separate HDs with an OS on each, Linux and XP.

Thanks.
Another Grub explanation: Grub allows you to boot one OS automatically *without* your intervention, and gives you the choice of booting your other installed OS' *with* your intervention.  You are presented with a menu during boot.  If you do nothing, it boots to your default OS.

Since you have two hd's & two OS', Grub would give you the choice without accessing the BIOS each time.

What is your purpose?

---

### Post by logos34 on 2007-06-15
> There are no entries for the grub boot menu - indeed, there is no menu at all.

Actually, there is.  You have 'hiddenmenu' option enabled (no hash # mark). So you're not going to see it, and even if you did it you'd only have 3 secs to choose another option than the first kernel.  
 
> default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**hiddenmenu**

Add a # in front of it and change the timeout to '10'.   At least for the time being until we get windows sorted.

Grub is definitely on sda, your linux drive (either on the mbr or the root partition).  

For some reason the ubuntu debian installer did not add a windows entry to menu.lst or fstab.  You could add it and see if you can boot XP via grub.  Then you can come back to the problem you're having with fixmbr on the windows disk (it is flagged 'primary bootable', so that's not the problem).  

Try adding this entry to the bottom of menu.lst:

**gksudo gedit /boot/grub/menu.lst**

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP
root		(hd1,0)
map            (hd1) (hd0)
map            (hd0) (hd1)
savedefault
makeactive
chainloader	+1

Then add this line to /boot/grub/device.map:
> 
(hd1) /dev/hda

Add a line to /etc/fstab:

> /dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

Then create the moutn point:
> sudo mkdir /media/hda1

See if you can boot into windows via grub now.

---

### Post by virtualy on 2007-06-16
Thanks, logos.  And others.

How do I modify the grub boot menu, and where do I find it?  I mean, I can see what you are referring to in the data I posted earlier.  I just don't know where that data came from.  I can look into my windows hd from linux.  I even copied the windows boot.ini file, thinking I might need to modify that.

[I][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect[/I]

I trust we are talking about the grub on the windows hd.  Or is it on both drives?  And, if on both drives, why don't I see a grub menu when I boot into Ubuntu?  Or is that hidden as well?

Sorry.  This is my first day with linux and I'm struggling up this steep learning curve.  I really appreciate you "holding my hand".

---

### Post by confused57 on 2007-06-16
> **virtualy said:**
> Thanks, logos.  And others.

How do I modify the grub boot menu, and where do I find it?  I mean, I can see what you are referring to in the data I posted earlier.  I just don't know where that data came from.  I can look into my windows hd from linux.  I even copied the windows boot.ini file, thinking I might need to modify that.

[I][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect[/I]

I trust we are talking about the grub on the windows hd.  Or is it on both drives?  And, if on both drives, why don't I see a grub menu when I boot into Ubuntu?  Or is that hidden as well?

Sorry.  This is my first day with linux and I'm struggling up this steep learning curve.  I really appreciate you "holding my hand".

Boot into Ubuntu...open Firefox,go to this thread in the forum, so you can copy & paste commands & Window's entry...then open a terminal(Applications---Accessories---Terminal), to edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
copy & paste one line at a time, press "enter" after each line
(the first line changes to the grub directory, the 2nd line creates a backup of your menu.lst)

then enter:
```
gksudo gedit menu.lst
```
this will open your menu.lst file, copy & paste the Window's entry I gave you in my other reply at the very bottom of your menu.lst

Also, as logos34 mentioned, find the line with hiddenmenu, then enter # in front of hiddenmenu.
Then change the timeout value to 10(it's probably set at 3)

quit & save...reboot & see if the changes displays your grub menu at boot & try to boot to Windows

Added:  Don't know what I was thinking(I wasn't), place a # in front of hiddenmenu:
```
#hiddenmenu
```

---

### Post by confused57 on 2007-06-16
Another thing you might want to do is enter bios setup & make sure the hard drive controller for your Window's drive is set to "auto"...yours might be "enabled" or "on"...
I had a problem with grub error 21 and this fixed it for me trying to boot Windows on a 2nd hard drive.

---

### Post by virtualy on 2007-06-16
Well, I am sending this from the Windows side.  I am forever indebted to you for your help.  Truly.

I'm assuming I can remove the # and reestablish hiddenmenu when I get around to a single OS, thereby avoiding the extra step(s) needed to deal with grub.

So, now I need to figure out Parallels...

Really guys, much obliged.

---

### Post by confused57 on 2007-06-16
> **virtualy said:**
> Well, I am sending this from the Windows side.  I am forever indebted to you for your help.  Truly.

I'm assuming I can remove the # and reestablish hiddenmenu when I get around to a single OS, thereby avoiding the extra step(s) needed to deal with grub.

So, now I need to figure out Parallels...

Really guys, much obliged.
Glad to help & that it worked...really there's no extra steps to using grub vs. changing bios.
If you want to boot Windows by default, read where to place your Window's entry in your menu.lst in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Windows will boot automatically, unless you enter your grub menu at boot by pressing "Esc" & select to boot Ubuntu.

If you're getting a grub menu when you boot first to your Window's drive, somehow grub was also installed to the mbr of the drive.  If that happens to be the case, you'd need to restore Window's IPL to your Windows drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Also, if you ever need to reinstall grub, you can use the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

When you have time, you might want to read the Grub section on this website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by logos34 on 2007-06-16
> I'm assuming I can remove the # and reestablish hiddenmenu when I get around to a single OS,

yep. and if you want to change the defualt selection just hit **Esc** key to bring up the grub menu . [edited]

So now that it boots into windows double check that you can still access Xp partition from linux.

---

### Post by logos34 on 2007-06-16
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect

is that the original, or did you edit that?

---

### Post by virtualy on 2007-06-22
> **confused57 said:**
> Glad to help & that it worked...really there's no extra steps to using grub vs. changing bios.
If you want to boot Windows by default, read where to place your Window's entry in your menu.lst in this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Windows will boot automatically, unless you enter your grub menu at boot by pressing "Esc" & select to boot Ubuntu.
...

Alright, I've followed the instructions, fiddled with the menu.lst file, and scratched my head - but I still get a grub menu that shows WinXP as the *last* selection, with Ubuntu as the default OS to load.  That's not going to work for my wife.

My set-up is as follows:

WinXP Pro on sata drive
Ubuntu on master IDE drive
Additional hard drive as Slave IDE drive

Here's the current iteration of my menu.lst file:

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I've left out the "makeactive" command because it seems to make no difference whether or not it's there.  ??  I've also left the slave IDE drive out of the grub selections, mostly because I have no idea how or why to put it in.

I've tried *mapping* (hd0) (hd1), (hd1) (hd0) - as shown; and the other way around - (hd1) (hd0), (hd0) (hd1).  Does that make sense?  In both instances, I get the same grub selections, in the same order.  IOW, it seems to make no difference how I map the menu.lst file.

My wife is computer knowledge adverse; she loves her email, web sites, and Photoshop but will not happily accept having to sit and wait for the grub screen, then select WinXP from the boot list, every time she wants to fire up the computer.  It would be much better for all concerned if I could make WinXP the default selection in grub, with some easy way for *me* to boot the Ubuntu drive, as **confused57** seems to be suggesting.

I hope this wasn't too...confusing.

Thanks.

---

### Post by virtualy on 2007-06-22
I should add that I have selected to boot from IDE Master (Ubuntu drive) in BIOS.  Also, as is no doubt apparent, grub is on the same IDE Master.

---

### Post by confused57 on 2007-06-22
> My wife is computer knowledge adverse; she loves her email, web sites, and Photoshop but will not happily accept having to sit and wait for the grub screen, then select WinXP from the boot list, every time she wants to fire up the computer. It would be much better for all concerned if I could make WinXP the default selection in grub, with some easy way for me to boot the Ubuntu drive, as confused57 seems to be suggesting.


What you can do is copy&paste your Window's entry above the line ###BEGIN AUTOMATIGIC KERNELS LIST, set the Default to 0.  You could remove the # in front of hiddenmenu, set the timeout to something like 3 seconds...Windows would automatically boot from grub, you wouldn't have the grub boot menu displayed, unless you press "Esc" within 3 seconds when prompted during bootup...when you press "Esc", the timer stops,then you could select to boot Ubuntu.

---

### Post by virtualy on 2007-06-22
> **confused57 said:**
> What you can do is copy&paste your Window's entry above the line ###BEGIN AUTOMATIGIC KERNELS LIST, set the Default to 0.

I'm sorry, when you say default, are you speaking of modifying this line:

root (hd1,0)

to read:

root (0)

?

---

### Post by confused57 on 2007-06-22
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default         0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout         3**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**hiddenmenu**
```

This section in your /boot/grub/menu.lst should look like the above.  Find the line ###BEGIN AUTOMAGIC KERNELS LIST, copy & paste your Window's entry to just above this line....you can leave the Window's entry at the very end of your menu.lst, if you like...won't hurt anything to leave it there.

---

### Post by dannyboy79 on 2007-06-22
> **logos34 said:**
> yep. and if you want to change the defualt selection just hit   key to bring up the grub menu .

So now that it boots into windows double check that you can still access Xp partition from linux.
you may want to edit the post that I am quoting as it says, "just hit key to bring up the grub menu" It should say, "just hit esc key........." this way if other's happen upon this they'll know what to do to envoke the grub menu.

---

### Post by virtualy on 2007-06-22
> **confused57 said:**
> Find the line ###BEGIN AUTOMAGIC KERNELS LIST, copy & paste your Window's entry to just above this line....

Aaaahh...

Didn't realize I needed to move the entry.  It was at the end of the menu.lst file.  I've moved it to where you suggested and got exactly the result I was looking for.

Forever indebted.

Not to beat this horse too hard but I have one more thing to do and then I won't bother y'all again.

For awhile.

As stated previously, my set-up is as follows:

Sata drive = WinXP
Master IDE = Ubuntu
Slave IDE = spare drive.

The spare drive has a prior WinXP, from which I am migrating all data to the sata drive.  Until I complete the migration, it would be nice to be able to boot directly into the old WinXP.  So, how do I rewrite the grub file so that it will preferentially boot to the old XP (Slave IDE), giving Ubuntu (Master IDE) as a second choice and the new WinXP (sata drive) as last choice?  Can I even do this (have three drive choices to boot into)?

Thanks for all of your help.

---

### Post by confused57 on 2007-06-23
First, you'll need to find an entry to boot your old XP, maybe something like this?:
```
title Microsoft Windows XP old
root      (hd2,0)
savedefault
map       (hd0) (hd2)
map       (hd2) (hd0)
chainloader +1
```

Make sure to make a backup of your menu.lst before editing...if the above entry boots Windows on your slave drive...you could place it above the ###AUTOMAGIC... line and move your SATA drive Window's entry to the very bottom of your menu.lst?

---

### Post by virtualy on 2007-06-23
> **confused57 said:**
> First, you'll need to find an entry to boot your old XP, maybe something like this?:
```
title Microsoft Windows XP old
root      (hd2,0)
savedefault
map       (hd0) (hd2)
map       (hd2) (hd0)
chainloader +1
```

Make sure to make a backup of your menu.lst before editing...if the above entry boots Windows on your slave drive...you could place it above the ###AUTOMAGIC... line and move your SATA drive Window's entry to the very bottom of your menu.lst?

That's great but it looks like it will only provide options for booting into the old XP or Ubuntu.  Is there any way to have all three options available (old XP, new XP, Ubuntu)?

Also, is there someplace you could refer me to so that I can read about just what these instructions mean?  I'd like to be able to figure this out on my own without pestering this board.

Not that I'm not *extremely* grateful...

---

### Post by confused57 on 2007-06-23
> **virtualy said:**
> That's great but it looks like it will only provide options for booting into the old XP or Ubuntu.  Is there any way to have all three options available (old XP, new XP, Ubuntu)?

Also, is there someplace you could refer me to so that I can read about just what these instructions mean?  I'd like to be able to figure this out on my own without pestering this board.

Not that I'm not *extremely* grateful...

Here you go:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
everything you always wanted to know about grub, and more...you're not pestering, you probably wouldn't be getting any replies if that were the case.

---

### Post by virtualy on 2007-06-23
> **confused57 said:**
> Here you go:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
everything you always wanted to know about grub, and more...

**YES!!!**  I *get* it now.

That link:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
should be placed in a sticky thread at the beginning of this board.  In fact, many of the helpful posts in this thread should be included as well.

A guggle thanks to you, **confused**, and to the others.

I feel so...empowered now.  Time to go add some color to my grub menu.

Eternally grateful for your patience.

-Paul

---

