---
title: "XP not loading"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by preciousnightmare on 2007-10-26
My grub seems to be messed up, I have XP and Ubuntu both on separate hard drives and when I pick XP on grub, it just goes back to grub making me choose between the 2 O/S. So I cant boot to XP but if I choose Ubuntu, I can boot there fine. Can someone help me out? I dont want to have to reinstall Ubuntu again :(

Here is my fdisk (if needed)

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29372936

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00025541

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24039   193093236   83  Linux
/dev/sdb2           24040       24321     2265165    5  Extended
/dev/sdb5           24040       24321     2265133+  82  Linux swap / Solaris


```

---

### Post by Maestro23 on 2007-10-26
Please post your menu.lst so someone can take a look at it.

> cat /boot/grub/menu.lst (lower case L)

---

### Post by preciousnightmare on 2007-10-26
Thanks for replying. Here is the menu.lst

```


gfxmenu /boot/grub/message.blusplash 

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
# kopt=root=UUID=81810f78-5bcb-4b46-996a-6d6cbf4ee5d9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=81810f78-5bcb-4b46-996a-6d6cbf4ee5d9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic
root=UUID=81810f78-5bcb-4b46-996a-6d6cbf4ee5d9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.binquiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

---

### Post by Pumalite on 2007-10-26
Backup menu.lst:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then edit:
gksudo gedit /boot/grub/menu.lst
Replace this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

For this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify            (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
makeactive
chainloader     +1

Save, exit, and reboot.

---

### Post by preciousnightmare on 2007-10-26
It's not working.  AFter doing all the changes you stated and rebooting, when choosing XP, it's still going back to the grub :(

---

### Post by Pumalite on 2007-10-26
Then move the Windows entry and place it after memtest but before END BEBIAN KERNEL...etc,etc
This time, just this:
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
makeactive
chainloader +1

Save, exit and reboot again.

---

### Post by meierfra on 2007-10-27
I looked at your September  thread ([http://ubuntuforums.org/showthread.php?t=544013]("http://ubuntuforums.org/showthread.php?t=544013")) where you  asked about dual booting vista and ubuntu. 
Was that a different computer? 
Also in that thread somebody suggested to install grub on (hd0,1).  Did you try something like that on your XP/Ubuntu computer?

---

