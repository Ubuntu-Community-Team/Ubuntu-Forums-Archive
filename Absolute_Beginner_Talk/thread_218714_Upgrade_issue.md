---
title: "Upgrade issue"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by ErsatzM on 2006-07-18
I just installed Breezy two nights ago, in a dual boot config with Windows XP, and subsequently upgraded to Dapper. However, after I upgraded and restarted the system, I see that the Breezy version is still listed on the boot loader menu. I'm looking to get rid of the breezy entry and just have the newest version listed. Any help? I'm a brand new Linux user, and although I have a fair degree of proficiency in Windows, I have no experiance in using a command line.

Otherwise, Ubuntu is looking and working fantastic. I got it installed and set up in dual boot without a single snag.

---

### Post by aysiu on 2006-07-19
Can you post the output of these two commands (just copy and paste the text into a post here)? ```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by Cariboo1938 on 2006-07-19
> **ErsatzM said:**
>  
Otherwise, Ubuntu is looking and working fantastic. I got it installed and set up in dual boot without a single snag.
I have Windows XP and Linux on my computer. I want to change from Linux Libranet to Ubuntu and I'm concerned about the "Dual Boot" set up, because several people are having problems with that. Can you please outline in detail how you set up the dual boot system?
Thanks
Juergen

---

### Post by ErsatzM on 2006-07-19
> **aysiu said:**
> Can you post the output of these two commands (just copy and paste the text into a post here)? ```
cat /boot/grub/menu.lst
sudo fdisk -l
```

For cat /boot/grub/menu.lst
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
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda6 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

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


```

For sudo fdisk -l
```

Disk /dev/hda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2573    20667591    c  W95 FAT32 (LBA)
/dev/hda2            2574        3739     9365895    5  Extended
/dev/hda5            3678        3739      498015   82  Linux swap / Solaris
/dev/hda6            2574        3676     8859784+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
64 heads, 63 sectors/track, 58145 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       58145   117220288+   7  HPFS/NTFS

```

---

### Post by ErsatzM on 2006-07-19
> **Cariboo1938 said:**
> I have Windows XP and Linux on my computer. I want to change from Linux Libranet to Ubuntu and I'm concerned about the "Dual Boot" set up, because several people are having problems with that. Can you please outline in detail how you set up the dual boot system?
Thanks
Juergen

I just know that it took inumerable web guides and a little bit of lucky tinkering. I'm surprised I got it running at all; I walked into the thing having zero prior experience. In the end, I don't even know what I did. When showing another noob (I'm assuming) how to install an OS, the last person you want helping you is another noob (especially one with only a few day worth of experience over you). Switching over from another linux distro puts this game in a completely different league. I wouldn't know where to begin... You're much safer working with some of the vets here.


EDIT: Actually, I did happen to find a minor (??) snag. When Ubuntu is loading and it is starting all those processes, it says "Starting PCMIA services ~~~~~ failed"

What does this mean?

---

### Post by aysiu on 2006-07-19
So what makes you think you're booting to Breezy? I see only one Linux partition, so there can't be a Breezy and Dapper simultaneously.

You do, however, have some old kernels in there. Just go to Synaptic (or Adept, if you're using Kubuntu) and search for *linux-image* and uninstall the older kernels.

---

### Post by ErsatzM on 2006-07-19
Thanks, that seemed to work fine. 
I didn't think I was booting to breezy. Just wanted to get it out of the menu.

Does anyone have suggestions on my other problem?

---

