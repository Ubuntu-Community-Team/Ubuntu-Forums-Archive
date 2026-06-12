---
title: "GRUB disk read error when dual-booting Windows"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Mike Tomasello on 2006-09-06
I got a brand new 160GB HDD for my laptop and decided to dual boot Windows and Ubuntu with a little extra space for maybe other distributions of Linux ... I've previously only been able to run one or the other because my HDD was small and I needed the space too much.

I set it all up with no problems and was able to boot into Ubuntu or WinXPHome just fine.

After having set-up both Ubuntu and Windows the way I wanted them (a process that seems to take an exceptionally long time on Windows; I was done after about eight hours of constant downloading and rebooting) and using it for a bit, upon restarting the computer and trying to boot into Windows as normal, I met with horror an error message after chainloader +1 on GRUB:

```

root (hd0,3)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

A disk read error occured
Press Ctrl+Alt+Del to restart

```

"No!" I exclaimed, booting into Ubuntu to see if I could find the problem.

But I'm stumped.

I can still access all the Windows files on its partition--NTFS--from within Ubuntu.

I've only been using Ubuntu for about a week collectivley now, so I'm still a bit of a beginner...

I've tried editing the GRUB menu.lst and changing 'root' to 'rootnoverify' as I've seen been recommended in threads with similar problems. While that removes the message about the unknown filesystem, it doesn't fix the problem.

Here's some extra information:

cat /boot/grub/menu.lst:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
# color cyan/blue white/blue

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
# kopt=root=/dev/hdc5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc5 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title         Ubuntu, kernel 2.6.15-23-386
root          (hd0,4)
kernel                /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc5 ro quiet splash
initrd                /boot/initrd.img-2.6.15-23-386
savedefault
boot

title         Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root          (hd0,4)
kernel                /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc5 ro single
initrd                /boot/initrd.img-2.6.15-23-386
boot

title         Ubuntu, memtest86+
root          (hd0,4)
kernel                /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc4
title           Microsoft Windows XP Home Edition
root          (hd0,3)
savedefault
makeactive
chainloader        +1

```

sudo fdisk -lu:
```

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63   209712509   104856223+  83  Linux
/dev/hdc2       209712510   230693399    10490445    5  Extended
/dev/hdc3       230693400   234886364     2096482+  82  Linux swap / Solaris
/dev/hdc4   *   234886365   312576704    38845170    7  HPFS/NTFS
/dev/hdc5       209712573   220202954     5245191   83  Linux
/dev/hdc6       220203018   230693399     5245191   83  Linux

```

From the above list, /dev/hd5 is where i have Ubuntu installed (/), /dev/hdc6 is an empty partition for possible future Linux distributions. They are both logical partitions of the extended partition /dev/hdc2. /dev/hdc3 is the 2GB swap partition, /dev/hdc4 is a ~37GB Windows partition (the one that doesn't work), and /dev/hdc1 is my /home/
partition (100GB).

If anyone can help, I'd be grateful.

Mike

---

### Post by rumli on 2006-10-29
I have the same problem.  Have you found a solution for this?

---

### Post by louieb on 2006-10-29
If i am not mistaken fdisk shows hdc# indicating the third harddrive.
and the grub entry is hd0,# indicating the first hardrive.
Which is it? Try hd2,# in your menu.lst file. Don't have any idea if it will work but it can't get any more broke.

---

### Post by Bachstelze on 2006-10-29
I think the problem is that your Windows is installed on a Logical partition. If I remember correctly, Windows can boot only from a Primary.

---

