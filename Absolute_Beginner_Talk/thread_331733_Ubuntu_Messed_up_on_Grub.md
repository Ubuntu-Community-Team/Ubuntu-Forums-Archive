---
title: "Ubuntu Messed up on Grub"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2007-01-05
Hello,
I'm making my second try at Ubuntu, but after the install, on booting, I got a Grub Error 25 when it trys to boot. I've tried reinstalling (I'm using the newest version, 6.10)
My Hard Drive configuration is as follows:
hda - one partition, ntfs with winxp - 80gb
hdb - 1st partition, fat32 with all my stuff on it 88gb
      - 2nd partition, ext3 with ubuntu installed, 88gb
      - 3rd partition, swap, 1gb

With my limited research on the live cd, I found that the problem probably lies with my menu.lst file.

Here is my menu.lst
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
# kopt=root=UUID=97a4a2ea-edc0-4a94-9ed9-76b064d9928f ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thanks A Lot In Advance,
Mikael

---

### Post by bodhi.zazen on 2007-01-05
Try changing > title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

to

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
splash
initrd		/boot/initrd.img-2.6.17-10-generic
# quiet
savedefault
boot
```

Or

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
# quiet
savedefault
boot
```

---

### Post by mikaelsnavy on 2007-01-05
Thanks for the reply,

I tried them both and had the same result, Grub Error 25

Any other suggestions?

Thanks for the help,
Mikael

P.S.
In the bios, It calls my 1st Hard drive is LBA and my second one is CHS, would that affect anything? I have had ubuntu installed before on the 1st hard drive.

---

### Post by diepruis on 2007-01-05
Does windows boot?

---

### Post by mikaelsnavy on 2007-01-05
no, it doesn't even get into grub

---

### Post by bodhi.zazen on 2007-01-05
Can you boot to the Ubuntu CD and post the output of:```
sudo fdisk -l
```

FYI : 
Grub Error 25: "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.

I just don't see it ...

Unless your root partition is not hdb2

And for what it is worth here is my stanza for Ubuntu:
> title		Feisty BASE kernel 2.6.20-2-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-2-generic root=/dev/sda6 ro quiet splash
splash
initrd		/boot/initrd.img-2.6.20-2-generic
savedefault
boot

---

### Post by mikaelsnavy on 2007-01-05
Here is is

```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       11534    92646256+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/hdb2           11535       23046    92470140   83  Linux
/dev/hdb3           23047       24321    10241437+  82  Linux swap / Solaris

```

My idea is maybe the ubuntu partition needs to come 1st because of how the boot partition needs to come before a certain point in CHS hard drives. Will GNOME Partition Editor do a non-destructive rearange?

Thanks,
Mikael

---

### Post by diepruis on 2007-01-05
Could you try commenting these lines?
```

title		Other operating systems:
root

```
They're near the bottom of the file.

---

### Post by diepruis on 2007-01-05
> **mikaelsnavy said:**
> My idea is maybe the ubuntu partition needs to come 1st because of how the boot partition needs to come before a certain point in CHS hard drives. Will GNOME Partition Editor do a non-destructive rearange?

If the BIOS cannot even load GRUB, I doubt that this is the problem.

---

### Post by mikaelsnavy on 2007-01-05
I commented out those lines but it still doesn't work (same error).

Do you want me to keep those commented out or restore the original state of the fiel?

Thanks,
Mikael

---

### Post by CroEragon on 2007-01-05
Try reinstalling GRUB. You can use great tool called SuperGRUB that is actually GRUB fixing tool that boots from LiveCD. If it can't help you, at least it will be   able to rewrite MBR and enable Windows if you for some reason need to bot into it (somebody else needs computer and cant use Ubuntu). It wil also be able to boot your Ubuntu  from hard disc so you will be able to use your CD drive amd when you boot from LiveCD you can't.
Download it from [here]("http://forjamari.linex.org/frs/download.php/458/sgd_0.9534_EN.iso")(it is .iso image that needs to be bourned to CD).

---

### Post by diepruis on 2007-01-05
> **mikaelsnavy said:**
> You want me to keep those commented out or restore the original state of the fiel?

Nah, you can uncomment them.

---

### Post by mikaelsnavy on 2007-01-06
OK, I finally fixed it. I booted to a XP disk and reinstalled xp's boot loader. I used partition magic to move the partition I planned to install ubuntu on to the start of the drive. Then I reinstalled ubuntu and it worked fine! I have no idea, but a clue is that now my bois list both of my drives as lba instead of one being chs. I don't care how it worked, I only care that I can now use ubuntu and still play my favorite windows games.
Thanks everyone for all your help,
Mikael

---

