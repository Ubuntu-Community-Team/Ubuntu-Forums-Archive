---
title: "Xubuntu intall trashed existing Ubuntu"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ah pook on 2008-02-08
ok. Two hard drives, a 120 g with a sweetly running ubuntu install, which is my main setup. That's hda, 
then I have an 80 g SATA drive used for whatever I feel like playing with. I installed Xubuntu from the live cd, to the 80g, sda, and now, while xubuntu runs fine, I can't get into the Ubuntu system. It boots, grub lets me select the ubuntu installation, i get the ubuntu splash screen, it goes away, then ......nothing.
Help. MY Entire life is on that disk....any ideas?

---

### Post by jaytek13 on 2008-02-08
Hm. I'm not entirely sure of the differences in why some OS's use sda while others use hda, but I do know that, for instance, if I install Ubuntu it labels all the drives in the hd format (hda, hdb, hdc), but if I say, install arch, it labels them all with the sd format (sda, sdb, sdc). For all intents between the two distro's hda = sda. 

So, I'd hate to suggest it, but you may have overwritten your Ubuntu install.

---

### Post by taurus on 2008-02-08
First of, you can still access all your personal file in Ubuntu from Xubuntu so it's not like they are gone UNLESS you accidentally installed Xubuntu on the same drive/partition as Ubuntu.

Did you install GRUB to MBR when you installed Xubuntu?  Can you boot into recovery mode with Ubuntu?

Otherwise, post the outputs of these commands from a terminal while you are in Xubuntu.

```
sudo fdisk -l
df -h
cat /boot/grub/menu.lst
```

---

### Post by ah pook on 2008-02-08
boy, you guys are fast. 

no i installed xubuntu on the same drive I've been using for a year now to play with various distros, while
keeping my original ubuntu  intact on the 120 gig drive. This never happened with any other install. Let me check out your suggestions tonight, as i'm at work now, stuck on an (shudder)XP machine...

thanks

---

### Post by ah pook on 2008-02-08
okay, I ran the commands, here's the results:



Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b081b07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13995   112414806   83  Linux
/dev/hdb2           13996       14593     4803435    5  Extended
/dev/hdb5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
geo@geo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.1G   65G   4% /
varrun               1008M   80K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   68K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hdb1             106G   79G   23G  78% /media/disk
geo@geo-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=2ca36701-a0ac-4f0e-94ec-cfd528279cca ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ca36701-a0ac-4f0e-94ec-cfd528279cca ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ca36701-a0ac-4f0e-94ec-cfd528279cca ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-rt (on /dev/hdb1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=72e19d48-8940-4695-9599-16c4192f19ff ro vga=795 splash 
initrd          /boot/initrd.img-2.6.22-14-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode) (on /dev/hdb1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=72e19d48-8940-4695-9599-16c4192f19ff ro single 
initrd          /boot/initrd.img-2.6.22-14-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu 7.10, memtest86+ (on /dev/hdb1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

geo@geo-desktop:~$ 

now what?

---

### Post by taurus on 2008-02-08
If you are in Xubuntu right now, /dev/sda1, it means your Ubuntu is resided on /dev/hdb1.  Looks like your Ubuntu is mounted to /media/disk.

```
ls -la /media/disk
```

---

### Post by ah pook on 2008-02-08
I downloaded Suuper grub disk, and let it do it's magic. Worked! I'm not sure what exactly it did, but now I can figure it out. thank you so much everybody for the help!

---

