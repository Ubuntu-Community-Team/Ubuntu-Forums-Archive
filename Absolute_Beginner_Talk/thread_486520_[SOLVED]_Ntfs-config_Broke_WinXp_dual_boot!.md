---
title: "[SOLVED] Ntfs-config Broke WinXp dual boot!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Funkey Monkey on 2007-06-28
Hi,

I recently in stalled ntfs-config. And now I can`t boot Win Xp. 

I`m using Ubuntu 7.04 and Win Xp pro both on 1 harddrive. I also have 2 other ntfs disks from my windoze days.

I have searched the net but found no help there for im forced to ask PLEASE HELP ME!!

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
Is a nice guide to Dual Booting Ubuntu and XP. 

It also contains other guides   
( [http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp](http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp) )

But after installing ntfs-config. There was no Winxp option in Grub. Therefore I followed the guide and now there is a Winxp option again but choosing it gives an "Error 13 : Invalid or Unsupported executable format"

---

### Post by louieb on 2007-06-28
Do i have this right. you had Dual booting working. The GRUB menu had entries for XP and Ubuntu, It would boot XP , you restart and it would boot Ubuntu?

Then you installed ntfs-config and after that the XP entry on the GRUB menu disappeared, you fixed the GRUB menu and now you get GRUB error 13 when you try to boot  XP? 

It makes no sense that installing ntfs-config would even touch your GRUB menu. What else did you do? Anyway  I suspect all thats wrong is your Grub menu entry is incorrect.  

1st look for a backup copy of /boot/grub/menu.lst. probably ends in **.bak or ~ **and compare XP entries.
IF that fails I need two things 1st a list of the partition table to get that open Applications>Accessories>terminal and run```
** sudo fdisk -l**
``` (lower case -L) post the output here. 
and post the /boot/grub/menu.lst file.

---

### Post by Funkey Monkey on 2007-06-28
Thanks for the reply. 

I`m a noob there for I don`t Know what I did wrong to break the window.

Yes windows did boot (dual boot), I did not use it or install any additional programs.
I am still trying to learn how to use Ubuntu and make it save (almost there). But then I needed to write some dvd`s and did not have time to read up on how to do it 100% so I wanted to boot windows and use the familiar programs that I Know and Trust.

I tried to find the backup of the grub menu but couldn`t.
 

1)sudo fdisk -l

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7354    59070973+  83  Linux
/dev/hdb2   *        7355        7541     1502077+  82  Linux swap / Solaris
/dev/hdb3            7542       14592    56637157+   7  HPFS/NTFS

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       30401   244196001    7  HPFS/NTFS


2)/boot/grub/menu.lst file.

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
# kopt=root=UUID=127b788c-8a79-4079-83a8-269816361b5e ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=127b788c-8a79-4079-83a8-269816361b5e ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=127b788c-8a79-4079-83a8-269816361b5e ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=127b788c-8a79-4079-83a8-269816361b5e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=127b788c-8a79-4079-83a8-269816361b5e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root 		(hd0,1)
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by louieb on 2007-06-28
Ok your partition table is kinda strange in that I would have expected to see a hard drive labeled /dev/hda. 
I am going to assume XP is on the same drive as Ubuntu here is what I want you to try. 
When the GRUB menu comes up highlight the XP entry and press** e** you are going to edit the root statement.   which currently is  **root 		(hd0,1) **highlight the root statement and press **e** again and change it to **root (hd0,2) **press enter then press **b** to boot. 
The reason for this is (hd0,1) is your swap partition. and it looks like XP is on the 3rd partition of that drive. If it boots then to make it permanent you will need to edit you /boot/grub/menu.lst and make the same change there. 
If it doesn't work then let me know what error you get and  post  your /boot/grub/device.map file. and we will check your other NTFS partitions for you XP install.

---

### Post by Funkey Monkey on 2007-06-29
Thanks a lot!!

Your advise work 100%, and I also understand what I did wrong. When I wanted to Boot Win it tried to the SWAP partition. Because  Ubuntu - hd 0,0
                                                           Swp  - hd 0,1
                                                          Windoze - hd 0,2

---

