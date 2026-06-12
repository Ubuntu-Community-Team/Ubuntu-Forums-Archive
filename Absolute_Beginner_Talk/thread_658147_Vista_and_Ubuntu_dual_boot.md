---
title: "Vista and Ubuntu dual boot"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by StormWatcher on 2008-01-04
I have been trying to have my system dual boot Vista and Ubuntu 7.10 for a couple of days.  I have tried everything I can think of and still no go.  It doesn't matter if I install Ubuntu or Vista first I still have the issue when I choose Vista from the Grub 1.5 menu, the system reboots.  I have a 400 GB SATA drive that I am trying to get both on.

Anyone have any suggestions?

---

### Post by kellemes on 2008-01-04
Not sure if this is going to help..
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by suomalainen on 2008-01-04
I built my own PC a few months back. Before I tried what you did I weighted all the feedback I received about dual booting via this forum.

I came to the conclusion that dual booting really served no purpose other then to show that "technically" it was possible to do. Additionally, having two operating systems on the same HDD meant Risk was high should a failure of some kind occur.

However, I still wanted the benefits that Linux-Ubuntu had to offer. Speading risk amongst two HDD seemed to be more appropriate. If one failed I still had another O/S/ to use while the other was being repaired.

I bought two 500GB Sata HDD's and installed each in it's own Mobile rack. With a turn of a key I can power the drive and operating syatem I want to use.

This method has worked extremely well for me and I would recommend it over dual booting any day.

Why would you want to put all your eggs in one basket anyway???

---

### Post by StormWatcher on 2008-01-04
I have no problem installing on two drive either.  I tried that method and still when I choose Vista on the Grub menu, it reboot and comes back to the Grub menu.

I want a dual boot because my wife uses the Vista for things like iTunes for the iPod and such and is far more comfortable with Windows.  I am trying to learn more about Linux, so I am trying to spend more time with it.  With a dual boot, my wife can reboot the Linux to the Windows and be happy.

The mentioned website is great but still does not solve my issue.  I used that site for the installing.  I have tried two different drives, I have tried one drive, they all have the same issue of rebooting as soon as I choose the Vista option in Grub.

---

### Post by bumanie on 2008-01-04
I had a dual boot system (feisty and xp) going that worked fine. It is generally accepted that you should install windows first, as windows will overwrite the mbr and thus also overwrite grub if linux is installed first.
If you are sure you want a dual boot system with vista it is possible, however the partitioning of the hard drive needs to be done from within vista. Go to disk management and find 'shrink volume'. Shrink to whatever size you want.
After you have done this, install ubuntu and grub should, recognise both OSes and give you the choice of which one to boot.
You could look at vmware or virtual box and run one OS in a virtual environment.

---

### Post by (((X))) on 2008-01-04
So, you can't boot  Vista?

reinstalling GRUB may help.

---

### Post by dstew on 2008-01-04
> when I choose Vista from the Grub 1.5 menu, the system rebootsYou mean, I think, that you get the grub menu again, correct? Or do you mean the system really reboots, going back to the BIOS screen, as though you cycled the power?

If it is just going back to the grub menu, maybe it can be fixed by editing the /boot/grub/menu.lst file. Post the output of the commands```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map
```

---

### Post by jonny5tails on 2008-01-04
Dear Stormy;
More details PLEASE!!!
It's so easy you could **** yourself.

---

### Post by meindian523 on 2008-01-04
> **dstew said:**
> Post the output of the commands```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map
```
> **jonny5tails said:**
> Dear Stormy;
More details PLEASE!!!

+1.
Please post what dstew asked for.

---

### Post by StormWatcher on 2008-01-04
When I say that the system reboots it goes through POST and everything again as if I hit the reset button.

I installed Vista first, defraged the drive and then used the Disk Manager to shrink the partition.  Then I used the Alternate install CD for 7.10 and installed.  It found the OS and modified the menu.lst on its own.

Here is the output you asked for:
```

$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74b3073

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24329   195418112    7  HPFS/NTFS
/dev/sda2           24330       30407    48821535   83  Linux
/dev/sda3           30408       48036   141604942+  83  Linux
/dev/sda4           48037       48641     4859662+  82  Linux swap / Solaris

Disk /dev/sdb: 4036 MB, 4036492800 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

```

$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=6f076a81-99db-48b1-aba0-5eb962f25e32 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6f076a81-99db-48b1-aba0-5eb962f25e32 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6f076a81-99db-48b1-aba0-5eb962f25e32 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista
rootnoverify            (hd0,0)
savedefault
makeactive
chainloader     +1

```
I also tried root (hd0,0) without the noverify and it still reboots when I select Vista.


```
$ cat /boot/grub/device.map
(hd0)   /dev/sda
```

I used to have it dual booting with XP Media and Ubuntu.  I have two SATA drives, but to figure out the issue I removed the one.  II then repartitioned the drive and installed a fresh copy of Vista Premium on the system.  I had a second drive in the system that I had originally installed Ubuntu on which was 75 GB.

Like I said, the system is down to one 400 GB drive.  I do not mind reinstalling, but it is getting old.

Let me know what else you need.

---

### Post by tylerspaska on 2008-01-04
wubi works great for me. it's not quite the same as an entire install, but it is exactly what i need. check it out. it makes a folder within windows and formats that folder to ext3. there is also a 7.10 version, but it is in the alpha stages.

[http://wubi-installer.org/](http://wubi-installer.org/)

also check out UNetbootin, i've never used it, but i hear it works well. 

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

as i said, i use wubi and i was able to install compiz-fusion with this howto

[http://ubuntuforums.org/showthread.php?t=643485](http://ubuntuforums.org/showthread.php?t=643485)

that gives me everything i wanted/needed from the 7.10 upgrade, now i'm more than happy to wait until alpha becomes beta (at least)

---

### Post by dstew on 2008-01-04
And, Ubuntu boots OK? From your description, it sounds like the problem is with the Vista boot sequence. That is, grub chainloads the first sector of the Vista partition, but when that sector runs, you get a hard reboot. You might need to restore the Vista boot sector. I believe that there is a FixBoot command on a Vista recovery console that can do this.

Can you boot Vista directly, using a Vista recovery disk or a supergrub disk? My guess is that trying this would give the same behavior. But I don't really know a lot about Vista booting...

---

### Post by StormWatcher on 2008-01-04
Yes Ubuntu works just fine.  I did boot off the Vista DVD and repair the boot sector from the repair options, however nothing changed.  

If I am not mistaken, because Vista is the first partition, isn't grub written tot he MBR where Vista was?  I am not familiar with how grub works or how Linux boots.  I do not have a floppy and I have not idea what a supergrub disk is.  So I am not sure.

---

### Post by dstew on 2008-01-04
Grub has several parts. The boot loader is stage1, and it goes into the first sector of the hard disk. That sector is called the Master Boot Record, and it is not part of any partition. The MBR also contains the partition table. When the disk boots, the BIOS executes the code in the MBR, which is grub stage1. Grub stage1 then (usually) loads stage1.5, which is in the next sector of the hard disk (still not part of any partition). Stage 1.5 then mounts the partition that was designated as root during the installation process, and runs the grub stage2. It is stage2 that displays the menu, and does the rest of the booting. The first sector of each *partition* is called the boot sector. Usually, grub leaves the Vista boot sector alone. The grub command chainload +1 means take the first sector of the designated root partition, put it into memory, and jump to it. At that point, grub is no longer in control of the boot process.

Did Vista boot without repairing the boot sector? I am running out of ideas. To me, your menu.lst seems correct.

Is your BIOS set to boot the disk, or a partition of the disk? Some BIOSes can boot a partition. If so, which partition is set to boot in the BIOS? This might be part of the problem, because then chainload +1 might be shooting at the wrong target. What I mean is that if by mistake you installed grub to the (hd0,0) partition, and set BIOS to boot this partition, then chainload +1 would be pointing to the wrong place.

---

### Post by StormWatcher on 2008-01-04
> **dstew said:**
> 
Did Vista boot without repairing the boot sector? I am running out of ideas. To me, your menu.lst seems correct.

Is your BIOS set to boot the disk, or a partition of the disk? Some BIOSes can boot a partition. If so, which partition is set to boot in the BIOS? This might be part of the problem, because then chainload +1 might be shooting at the wrong target. What I mean is that if by mistake you installed grub to the (hd0,0) partition, and set BIOS to boot this partition, then chainload +1 would be pointing to the wrong place.

I vaguely remember the install asking me where to install the boot loader and it defaulted to h(0,0).  I am reinstalling Windows right now and then I will run the install of Ubuntu Alternate again.  Should I install the boot loader to h(0,1)? 

```
$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74b3073

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24329   195418112    7  HPFS/NTFS
/dev/sda2           24330       30407    48821535   83  Linux
/dev/sda3           30408       48036   141604942+  83  Linux
/dev/sda4           48037       48641     4859662+  82  Linux swap / Solaris

Disk /dev/sdb: 4036 MB, 4036492800 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

---

### Post by StormWatcher on 2008-01-04
Too weird for me.  I installed Vista.  It works.  I used my alternate CD and did a recover broken system.  I reinstalled Grub.  Told Grub to install on (h0,1) and then rebooted.  I did get Grub come up and I choose Vista.  It booted!!!!

I was so excited!  But then I reboot and Grub is gone and it only boots Windows.  I think something is a little funny here.

So I go through the rescue again and reinstall Grub.  Install it on hd0,1 and reboot.  Straight to Windows it goes.  WTF!!!!!

---

### Post by Princey on 2008-01-04
You don't need to run the rescue again. If you booted fine, then try re-installing grub using a live cd using [this]("http://ubuntuforums.org/showpost.php?p=4051320&postcount=2") tutorial.

---

### Post by bharkins on 2008-01-04
I've gone around a bit on this issue and solved it with two key sources. Create the Super Grub Disk from [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml) which I found essential to get the boot files set up in both OS's. Then take a day to read Herman's web site all about Grub:  [http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub) -  a treasure trove of information.

---

### Post by dstew on 2008-01-05
> Told Grub to install on (h0,1) and then rebooted.That grub designation should have given you an error. To install grub, the designation should be (hd0) or (hd0,0) or (hd0,1).

My guess is that you installed it on (hd0,1). That is probably not the best way to go. That means you installed it into the /dev/sda2 partition, where Linux lives. When you rebooted the first time, your BIOS booted the /dev/sda2 *partition*, and you chose VIsta, and it worked. However, the second time you booted, it apparently booted the /dev/sda *disk* and went straight to VIsta. This happened because you did not install grub into the MBR of the disk, so the WIndows booter is still there.

Without changing anything in grub or your Ubuntu installation, you should be able to get it to work if you can tell your BIOS to boot the /dev/sda2 partition every time. If you cannot do that, you will need to re-install grub into the MBR of the /dev/sda disk. To reinstall grub to the MBR, first boot a LiveCD, open a terminal window, and enter **grub**. This will get you the grub command line, **grub>**. At the grub command line, enter```
root (hd0,1)
setup (hd0)
quit
```Remove the CD, and reboot.

---

### Post by StormWatcher on 2008-01-08
ARRRGGHHHH!!!!!

I did just as you instructed and now freaking Windows won't install.  I am back to where I was with it rebooting when I select Windows.

It now seems plainly obvious that I just need to buy a new computer to run Ubuntu and say screw the dual boot.  To recover Windows I have to do a new install.   Grrrrr.....

Thank you for the help.

---

### Post by wheels. on 2008-01-08
If you are having troubles with grub, you could try using the vista boot loader.
Download [Easy BCD]("http://neosmart.net/dl.php?id=1") and use this to configure the vista boot loader to boot ubuntu, as well try following [this guide]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") it will explain most things, If you want start from fresh and follow it and it should give you your dual boot configuration!!

Good luck!!

wheels.

---

### Post by StormWatcher on 2008-01-08
Actually I found the bootrec.exe command from the Vista disk letting me fix the MBR in Vista.  So I can keep trying and not loose all the stuff I installed last rebuild.

So with that...  Any more suggestions?

---

### Post by wheels. on 2008-01-08
Can you boot into windows?
if so download easyBCD and configure the windows bootloader to load ubuntu,
then should be problem solved/

---

### Post by StormWatcher on 2008-01-08
Thanks Wheels.  I just found that link last night before I saw your post.  I did use it and now it uses Vista to dual boot, but it dual boots!!!!

Thanks you all for your help.

---

