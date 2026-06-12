---
title: "Installed Ubuntu, Vista won't boot"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Tiwilager on 2008-04-15
Hello,

I have 2 hard drives in my computer, I had vista installed on one of them, and I then partitioned it to install Ubuntu on the same drive, to keep the other for data/backup.  After Ubuntu installed, when I chose vista from the boot menu, the computer simply restarts and enters the boot menu again, over and over again.  I am new to this, and I don't know where to start, thanks.

---

### Post by Inxsible on 2008-04-15
Can you login to Ubuntu?

if so post the output of the following command```
cat /boot/grub/menu.lst
```

---

### Post by Tiwilager on 2008-04-15
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
# kopt=root=UUID=c75c6cb0-fb6c-4d86-bf46-5908b4dacb8a ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c75c6cb0-fb6c-4d86-bf46-5908b4dacb8a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c75c6cb0-fb6c-4d86-bf46-5908b4dacb8a ro single
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
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Inxsible on 2008-04-15
Ok that looks good. Could you now post ```
sudo fdisk -l
``` Thats a lower case L

Use the code tags to post the output here.

---

### Post by Tiwilager on 2008-04-15
```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe49bd47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20555   165106445+   7  HPFS/NTFS
/dev/sda2           20556       30104    76702342+  83  Linux
/dev/sda3           30105       30515     3301357+   5  Extended
/dev/sda5           30105       30515     3301326   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedcdba18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30516   245114880    7  HPFS/NTFS

```

---

### Post by Francisck on 2008-04-23
I have the same problem. I have two hard drives one has my vista install the other my ubuntu. Right after I installed ubuntu my vista boot loader no longer works. I of course tried booting from my vista DVD and tried \boot/bootsect.exe/nt60 all and \boot/bootrec.exe/FixMbr and I restarted...my grup still runs and i added my vista install to it however i get an error that says bootmbr is missing please ATL-CRL-BACKSPACE to restart..

Am i doing something wrong?

Should I uninstall grub and/or linux all together?\

Best Regards,
Francisco

---

### Post by mauro235 on 2008-04-27
I have extactly the same issue. After installing Ubuntu (the same happens with Fedora) Windows Vista (and, the same happens with XP) won't boot. Instead of booting, it reboots and goes to grub.

This doesn't happen with OpenSuse, and that's kind of weird.

If i boot with vista dvd (or XP cd) and do the "bootrec /fixboot" and "bootrec /fixmbr" thing in the repair console, it works, but it screws grub. I can't dual boot.

Anyone had the same problem and could do something to dual boot?

I'll leave my system specs:

```

ECS P965T-A Motherboard
DualCore Intel Core 2 Duo E6300, 1866 MHz (7 x 267)
DIMM1: Kingston 9905316-005.A04LF
DIMM2: Kingston 9905316-005.A04LF
DIMM3: OCZ Value OCZ26671024V
North Bridge: Intel Broadwater P965
South Bridge: Intel 82801HB ICH8
ATI Sapphire Radeon X1600 XT 256 MB

```

---

### Post by darkwalk on 2008-04-27
Same problem here. Fortunately, I ghosted my Xp partition before installing ubuntu. I restored the image and installed XOSL instead of grub and it worked.

---

### Post by Aurora@FleetBuzz on 2008-05-01
If you haven't got this solved yet, here's a link on how to repair your Vista bootloader.
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
You might want to try to reinstall Ubuntu after that and see if GRUB identifies it.  The Vista repair is very simple (speaking from experience).

---

