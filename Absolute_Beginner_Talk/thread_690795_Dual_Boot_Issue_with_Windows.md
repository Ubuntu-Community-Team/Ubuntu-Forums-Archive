---
title: "Dual Boot Issue with Windows"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Ohioan on 2008-02-07
I partitioned my HD with 29g Windows, 1g Swap and 30g for Linux.  

Now, Ubuntu 7.10 opens perfectly fine but windows doesn't.  When I select windows in GRUB, it goes to a black screen with white lettering in the upper left corner that says "starting up" but doesn't move from there.  

Anyone have any ideas?

---

### Post by Ex-windows on 2008-02-07
. Have you tried the super grub disk?? Here is a good link for dual boot issues
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/). There should also be a link to download the super grub disk. That will/should get you into your windows partition.

---

### Post by Ohioan on 2008-02-08
I've looked into Supergrub, but everything i've read seems to be about fixing Linux boots.  I'll have to download it and see what I can come up with.

---

### Post by dstew on 2008-02-08
You can probably get Windows to boot by editing the /boot/grub/menu.lst file. If you want to try that, post to the forum the results of the commands```
sudo fdisk -l
cat /boot/grub/menu.lst
```and we can give you some advice on what to do.

---

### Post by Ohioan on 2008-02-09
Here are the results

> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a8a75c1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3516    28242238+   7  HPFS/NTFS
/dev/hda2            3645        7296    29334690   83  Linux
/dev/hda3            3517        3644     1028160   82  Linux swap / Solaris

Partition table entries are not in disk order
odellz@odellz-laptop:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=6716750d-e563-4425-8832-daad3303825c ro

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
# defoptions=splash vga=791

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6716750d-e563-4425-8832-daad3303825c ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6716750d-e563-4425-8832-daad3303825c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

odellz@odellz-laptop:~$ 


---

### Post by Ohioan on 2008-02-09
Does my problem have to do with the fact that there is no entry for "make active"?  

I edited the menu.lst to make Ubunu boot faster.  When I saw the thing about windows I didn't think it looked right, but I have no idea what was wrong so I didn't mess with it at all.

---

### Post by dstew on 2008-02-09
> Does my problem have to do with the fact that there is no entry for "make active"? No, that entry is just as it should be. It has no argument. It just tells grub to make active the partition designated by the root statement.

The entry in the /boot/grub/menu.lst file looks correct. Try booting Windows from the Recovery Console on your WIndows CD. Maybe there is a problem with Windows itself.

---

### Post by Ohioan on 2008-02-09
Uhg!  You mean I have to dig to find my Windows CD?!?!  Man..  I havn't had that thing in...  well... probably 2 years.. since I bought this hunk of junk.

Thanks for the help though!

---

### Post by Ex-windows on 2008-02-09
> **Ohioan said:**
> I've looked into Supergrub, but everything i've read seems to be about fixing Linux boots.  I'll have to download it and see what I can come up with.

The super grub disk will also get you into your windows side. It has an option to "boot" windows. This way you could look there as well as in your ubuntu side to check for problems.
It can also Fix some grub issues. Which you can read more about on the link in my  previous post.
Good luck

---

### Post by Ohioan on 2008-02-13
Well, I tried to boot windows with Super Grub Disk, and it would run a script that ended with a "boot" and nothing would happen.

---

### Post by adrian15 on 2008-02-14
> **Ohioan said:**
> Well, I tried to boot windows with Super Grub Disk, and it would run a script that ended with a "boot" and nothing would happen.

Try **Super Grub Disk -> Super Grub Disk (With Help) -> Windows ->Windows (Advanced) -> Activate Windows partition**   and try again that: **Super Grub Disk -> Super Grub Disk (with Help) -> Windows -> Boot Windows ** option.

Do you have perhaps a recovery partition and you should use the Boot Windows from 2nd partition (laptop) option?

adrian15

---

