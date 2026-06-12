---
title: "Dual-Boot Problems"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by deviantnz on 2007-04-28
Ok so I'm trying to dual boot xp and ubuntu. So far i've installed xp on one partition and ubuntu 7.04 on another. 

At the moment when I start my computer up it just loads up straight away into windows xp without giving me an option to choose Ubuntu.

I've taken this screen shot to confirm that my partitions are set up correctly. I used the live cd to take this.

[IMG]http://static.imgfly.com/2007/04/28/7208/Screenshot.jpg[/IMG]

I have been reading about GRUB but I'm not 100% what I'm suppose to do with it. If anyone could give me some easy to follow advice I would be very great full.


Thanks

Mike

---

### Post by overdrank on 2007-04-28
> **deviantnz said:**
> Ok so I'm trying to dual boot xp and ubuntu. So far i've installed xp on one partition and ubuntu 7.04 on another. 

At the moment when I start my computer up it just loads up straight away into windows xp without giving me an option to choose Ubuntu.

I've taken this screen shot to confirm that my partitions are set up correctly. I used the live cd to take this.

[IMG]http://static.imgfly.com/2007/04/28/7208/Screenshot.jpg[/IMG]

I have been reading about GRUB but I'm not 100% what I'm suppose to do with it. If anyone could give me some easy to follow advice I would be very great full.


Thanks

Mike

Hi I am not a feisty expert but it appears you have two partitions on the drive correct? Did you install the grub on that drive or do you have other drives? You may find some help with this link to find and reinstall your grub!
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!:)

---

### Post by freebird54 on 2007-04-28
The set up looks quite workable.  I suspect that grub (the boot loader) got written over in the Windows install procedure.  Here's a link to one way to fix it.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Actually there is a lot if grub (and other) info on thos pages - so it may be more help than just now.

Post back with results/problems...

Hope it helps!

---

### Post by redgilda on 2007-04-28
I have the same problem.

I've had Windows installed for many months. Then Installed Ubuntu few days ago - all went correct but when I start the pc - it goes directly to Windows. So I tried reinstalling Grub following the many threads about it - said all is complete but still grub doesnt load.

I'll try posting the 'layout' of my pc - ive got many drives and many partitions so maybe someone can help me find out WHERE exactly I should install GRUB to, so that it loads correctly.........

---

### Post by Legionox on 2007-04-28
To fix this problem first boot to your Ubuntu installation disk, then start a Terminal Window (Applications->Accessories->Terminal)
Run the command```
grub
```
Now enter```
find /boot/grub/stage1
```
You should end up with a result looking like "(hd0,1)"
Now enter```
root (hd0,1)
```
(Replace hd0,1 with the result you received)
Now enter```
setup (hd0)
```
Enter```
quit
```then```
exit
```
and reboot your computer:)

---

### Post by redgilda on 2007-04-28
So here it is.. like I said above - I had WinXP on one partition and installed Ubuntu on another (all went well) but only Windows boots, without even going into the grub menu

I've got 3 hard drives (1 SATA, 2 ATAs)

here's my fdisk output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19929   160079661    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2165    17390331    7  HPFS/NTFS
/dev/sda2            2166       19457   138897990    f  W95 Ext'd (LBA)
/dev/sda5            2166       16755   117194143+   7  HPFS/NTFS
/dev/sda6           16756       19308    20506941   83  Linux
/dev/sda7           19309       19457     1196811   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2499    20073186    c  W95 FAT32 (LBA)
/dev/hdb2            2500        4997    20065185    f  W95 Ext'd (LBA)
/dev/hdb5            2500        4997    20065153+   b  W95 FAT32
ubuntu@ubuntu:~$ 
```

I even re-did the solution above (again) - again - no problems, grub installed blah blah - still boots into Win directly.

here's my grub file

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
# kopt=root=UUID=9ce07c6d-d4c6-42b3-9279-9139177f4b13 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,5)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9ce07c6d-d4c6-42b3-9279-9139177f4b13 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9ce07c6d-d4c6-42b3-9279-9139177f4b13 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

any ideas? heeeeeeeelp (will be much appreciated, I wanna test FF at last!!)

---

### Post by sailor2001 on 2007-04-28
what has always worked for me is to download and burn a simply MEPIS disk and use that to do any repair....grub boot repair in that is listed under instalation center    also you could download SUPER GRUB and burn that disk

---

### Post by deviantnz on 2007-04-28
Thanks for all the replies!

I followed Legionox's instructions to reinstalling GRUB. I should point out on the first line entering just 'grub' into the terminal window didn't work for me. It had to be 'sudo grub'.

Anyway i restarted and GRUB loaded up :). But now I'm having the opposite problem.  I can load up Ubuntu fine but there is no option to load XP. Is it possible to add the XP entry into GRUB?  


Thanks

Mike

---

### Post by freebird54 on 2007-04-28
No other answer yet - so here goes.  You need to add in the instructions to boot Windows.  AFTER the lines reading:

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

you should add back in the lines about booting your OS (as in the post earlier)  ensuring that the drive they refer to is the correct one.

---

### Post by deviantnz on 2007-04-28
Thanks for your help it's all working now.

I'll post what I did in case anyone is having similar problems.

1. Open up terminal

2. Type in:
```
sudo gedit /boot/grub/menu.lst
```

3.  Gedit should open. Scroll down till you see 

# ## End Default Options ##

and add this code below it.

```
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

4. Save document and reboot.


Thanks

Mike

---

### Post by redgilda on 2007-04-29
> **deviantnz said:**
> and add this code below it.

```
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```
4. Save document and reboot.
Thanks
Mike
Well, I do have this section in my menu.lst - like I posted above (though it looks a bit different probably due to diff OS and other stuff) yet its still not working for me... :(

---

### Post by redgilda on 2007-04-29
ok, finally sorted it out. Like I said I have 3 Hard drives and well, Bios was set to boot from the drive with 'Windows' and Linux files on it - BUT seems like grub installed on another drive - the one with the 1st letter of the alphabet I was using (even though there were no operating systems on it, just data) - so when I switched the BOOT priority drive in Bios - it worked. I was presented with a nice Grub menu to choose from both Linux and Windows :)

---

