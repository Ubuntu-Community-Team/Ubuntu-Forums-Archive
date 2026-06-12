---
title: "WinXP / Unbuntu 7.04 Dual Boot - Grub Error 21"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by matthewpetty on 2007-05-22
Hello,
I'm having big troubles. I ran the Ubuntu LiveCD on my WinXP box, and after playing with it, decided to install on a separate internal HDD. So I ran install, installed 7.04 on a different hdd from Windows, accepted the default GRUB settings, and now when I boot, I get 'grub error 21'. Neither WinXP nor Ubuntu will start. I can boot the LiveCD though, so I did and Googled the grub error, and found several possibilities.

Please can someone help me? This is my only computer.

Here's what I've already tried. These are based on forum threads elsewhere.
1. FreeDOS boot CD - can't access RAID drive.
2. Ubuntu LiveCD - can't access RAID drive.
3. MSDOS boot floppy - can't see HDDs
4. ntdetect.com on a floppy - keeps rebooting.
5. WinXP recovery floppy - don't have one. My machine came with WinXP preinstalled, and a receovery CD which doesn't give me an option  to fix my MBR, which is what it seems to need.

I think the problem may be due to the box having a RAID main drive. I wasn't aware how tricky these could be. Here's some info...

Here's the output from sudo fdisk -l: -------------------------

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9588    77015578+  83  Linux
/dev/sda2            9589        9963     3012187+   5  Extended
/dev/sda3            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table
-----------------------------------------------------------

As you can see, sdb and sdc are two 250GB hdds, in a RAID array. The machine was prebuilt, and just worked, so I don't know anything about it.

Here's my grub menu.lst: ----------------------------------------------
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
timeout		3

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
# kopt=root=UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

END OF MENU.LST -------------------------------------

Any ideas on how to change menu.lst to run Ubuntu? Or even just get rid of Ubuntu and GRUB and go back to WinXP single boot?
Please can anyone help? Any more info needed?

Matthew

---

### Post by Borzo on 2007-05-22
Your root enteries are not set up correctly, and you do not have an entery for windows.

1 boot live CD

2 start the terminal

3 sudo vol_id /dev/sda1 | grep UUID
   sudo vol_id /dev/sda3 | grep UUID
   
   write down the UUID given, you will need them later

4 mount /dev/sda1 with:
   sudo mkdir /mnt/linux && mount /dev/sda1 /mnt/linux 

5 edit /boot/grub/menu.lst with:
   sudo nano /mnt/linux/boot/grub/menu.lst

change root (hd2,0) in the linux enteries  to root (hd0,0)

add this to have windows in the grub menu, after the last linux entery

title Windows XP
root (hd1,0)
makeactive
chainloader +1

save & exit

6 edit /etc/fstab with:
   sudo nano /mnt/linux/etc/fstab
   change the UUID numbers for /dev/sda1 and /dev/sda3 to those you wrote down in step 3

save & exit

7 sudo umount /dev/sda1

8 reboot

At the grub countdown press ESC to access the boot menu, and try either linux or windows, see if anything works/changes. The menu will boot by default to linux if you don't press ESC.

---

### Post by matthewpetty on 2007-05-23
Hi, thanks for your detailed solution. I'm in the middle of trying it now. Here's how I'm doing.
1. done
2. done
3. It appears that the sda,b,c etc changes each time I restart the LiveCD. When I tried this at first, sda1 was WinXP, and sdc1 & 3 was the Linux drive. So I rebooted to make things easier. When I did, the sda1 & 3 were now the Linux volumes. I wrote down their UUIDs as described.
4. done. I had to do this in two parts, because the first time it said "only root can do mount". So I did the 2 commands separately.
5. edited the file (although I used gedit, because I don't know nano - sorry!). made hd2 changes, and added windows entry. See changed part of file below:

----------------
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd1,0)
makeactive
chainloader +1
----------------

6. opened /mnt/linux/etc/fstab and it looks like this:

----------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=6d03ce2a-8a7a-4ff8-b055-b5a617cea109 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=9334459a-f788-4cff-bdc2-3557c218a81a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
----------------

No mention of sda1 or sda3! As it happens, the UUID listed for sdc1 is the correct UUID for the Linux Boot volume, and the UUID for sdc5 (!) is the correct UUID for what should be sda3. So, I'm changing the ref to sdc1 to sda1, and sdc5 to sda3. Wish me luck.

7. done
8. HERE GOES...

---

### Post by matthewpetty on 2007-05-23
Just rebooted, no luck. Still getting Grub Error 21.

So I've rebooted again with the LIveCD to see what's up. fdisk tells me that sdc1 and sdc3 are now the Linux volumes again.

I've looked around, and device.map seems to define what hd0 and so on are. But if this changes each time, how can I make it work? Contents of device.map here:
-----------
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
-----------

menu.lst and fstab are the same as after I edited them, of course, because they are on the internal hard drive.

Any ideas? Thank you for any more help.

Matthew

---

### Post by Borzo on 2007-05-23
hmm... it's difficult for me to take this on as i don't have RAID, but take a look at this post and see if  it helps your situation:

[https://launchpad.net/ubuntu/+source/grub/+bug/8978/comments/14](https://launchpad.net/ubuntu/+source/grub/+bug/8978/comments/14)

good luck

---

### Post by nucleararms on 2007-05-23
I have the same infinite loop error but I'm not using RAID. I was just wondering if either of you guys know of an upstream source that fixes that or could just tell me if I need to reinstall grub or not? Thanks any response is much appreciated!
-arms

---

### Post by Borzo on 2007-05-23
> **nucleararms said:**
> I have the same infinite loop error but I'm not using RAID. I was just wondering if either of you guys know of an upstream source that fixes that or could just tell me if I need to reinstall grub or not? Thanks any response is much appreciated!
-arms

error 21 means that a drive is not found by grub, in most cases it means there is an error in /boot/grub/menu.lst you need to check that against your drives layout.

It also depends on when error 21 is displayed, do you get grub's menu or does it hapen before that?

---

### Post by confused57 on 2007-05-23
> **matthewpetty said:**
> Just rebooted, no luck. Still getting Grub Error 21.

So I've rebooted again with the LIveCD to see what's up. fdisk tells me that sdc1 and sdc3 are now the Linux volumes again.

I've looked around, and device.map seems to define what hd0 and so on are. But if this changes each time, how can I make it work? Contents of device.map here:
-----------
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
-----------

menu.lst and fstab are the same as after I edited them, of course, because they are on the internal hard drive.

Any ideas? Thank you for any more help.

Matthew

Here are several ways to reinstall Window's IPL code to the Window's drive mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or you can use the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The one time I received grub error 21, one of my hard drives was "off" in bios...changed it to "auto", which corrected the error.

Another thing you might try is to install grub to the linux drive mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
which would be something like this:
```
sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit
```
then go into bios and set your Linux drive as the first hard drive booted...if you get a grub boot menu, highlight the Ubuntu entry, press "e", and make sure root is (hd0,y), then press "b" to boot...this change is temporary if it works, but can be made permanent.

---

### Post by matthewpetty on 2007-06-05
Thanks for all your responses. I've been away on holiday, so I haven't looked at this again until now. OK. After reading about the BIOS order of hard drive boot, I changed this in my BIOS so the Ubuntu drive boots before the WinXP RAID. When I restarted, it booted into Ubuntu! :D

But! I had forgotten my login password. That's what happens when I go away on holiday. :oops:

So, with my first boot drive now set to the correct one, I rebooted using the LiveCD, and reinstalled Ubuntu, giving myself a new username and password. When that was done, and I rebooted, I checked the GRUB menu, and WinXP wasn't on there. Now I can imagine why that is, because Ubuntu can't see the RAID drive where it lives.

Ubuntu now works fine, but how do I add WinXP to the GRUB menu? How do I know what volume/drive codes to use? Also, how do I change the default GRUB boot?

---

