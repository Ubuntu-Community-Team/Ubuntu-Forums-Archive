---
title: "Problem... Help!!!"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by lee101 on 2006-10-09
i have ubuntu and windows, but someone was on my computer and selected the wrong windows from the grub menu, after that grub was gone so i had to re install that from the live cd, but, the windows im using is like a demo version everything needs installing again e.g msn messenger.
i used to have 4 acounts 2 select from when i had windows but now it just selects the admin automatically.

can any 1 recover my windows:mad: :mad: :mad: 

please leave ur comments, it has been like this 4 quite some time now:mad: :mad: ](*,) ](*,)](*,)

---

### Post by wieman01 on 2006-10-09
Please show us the contents of the GRUB config file by running this command from a terminal window:
> sudo gedit /boot/grub/menu.lst

---

### Post by lee101 on 2006-10-12
```
#menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda4 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/hda4 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```

---

### Post by lee101 on 2006-10-12
^^^^
that is what comes up wieman01

---

### Post by PriceChild on 2006-10-12
i can't quite seem to understand the problem... Someone else has installed another version of windows onto your computer? So select the correct one from the grub menu on bootup.

---

### Post by wieman01 on 2006-10-12
I don't seem to undersand your problem, either. Can't you select Windows when GRUB appears on the screen and boot up Windows? Have you installed VISTA?

---

### Post by Brunellus on 2006-10-12
> **lee101 said:**
> i have ubuntu and windows, but someone was on my computer and selected the wrong windows from the grub menu, after that grub was gone so i had to re install that from the live cd, but, the windows im using is like a demo version everything needs installing again e.g msn messenger.
i used to have 4 acounts 2 select from when i had windows but now it just selects the admin automatically.

can any 1 recover my windows:mad: :mad: :mad: 

please leave ur comments, it has been like this 4 quite some time now:mad: :mad: ](*,) ](*,)](*,)
I think I understand what happened.

Many "mass-market" computers now being sold ship with a recovery partition on their main hard drive;  booting this recovery partition will trigger a complete wipe and re-installation of Windows on the main hard drive partition.  

GRUB reflects this by showing TWO windows kernels--one "regular" Windows kernel and a second one, the recovery one, which is not explicitly identified as such.

If this is what happened, then you will find that GRUB doesn't even start up when you power up the computer--it will boot directly to Windows using Windows' own bootloader.  

If this is in fact what happened, then I am sorry to tell you that you have lost whatever data you had on your previous Windows install. You probably also lost your Linux partition(s), but I'm not so sure.

---

### Post by wieman01 on 2006-10-12
> **Brunellus said:**
> I think I understand what happened.

Many "mass-market" computers now being sold ship with a recovery partition on their main hard drive;  booting this recovery partition will trigger a complete wipe and re-installation of Windows on the main hard drive partition.  

GRUB reflects this by showing TWO windows kernels--one "regular" Windows kernel and a second one, the recovery one, which is not explicitly identified as such.

If this is what happened, then you will find that GRUB doesn't even start up when you power up the computer--it will boot directly to Windows using Windows' own bootloader.  

If this is in fact what happened, then I am sorry to tell you that you have lost whatever data you had on your previous Windows install. You probably also lost your Linux partition(s), but I'm not so sure.
You must be kidding me... This is the first time I hear of something like that. Honestly this is shocking... Why would anybody buy a computer with a recovery partition that eliminates the previous install of Windows and all their personal data? That - by all means - defeats the purpose, now doesn't it?

Thanks for this information. I would have never anticipated something like that.

---

### Post by Brunellus on 2006-10-12
> **wieman01 said:**
> You must be kidding me... This is the first time I hear of something like that. Honestly this is shocking... Why would anybody buy a computer with a recovery partition that eliminates the previous install of Windows and all their personal data? That - by all means - defeats the purpose, now doesn't it?

Thanks for this information. I would have never anticipated something like that.
By "recovery" essentially what I mean is "a replacement for the install CDs."  No attempt is made to rescue data--it's a straight up wipe & OEM install.  The only difference is that the installation files are drawn from the 'recovery' partition and not CDs.

---

### Post by paulius2003 on 2006-10-12
Yes I have seen such things, especially on HP and Compaq computers.  Is it possible to delete the partition in Disk Management in Windows? That way you can free up the 10gb or whatever the size is.

---

### Post by d3v1ant_0n3 on 2006-10-12
So there's not even a repair install option available? That sounds horrendous! I found the official OEM 'recovery' cd that came with this machine bad enough...It took ages longer to install, and insisted on having Norton A/V installed by default. That was fun.

---

### Post by wieman01 on 2006-10-12
> **Brunellus said:**
> By "recovery" essentially what I mean is "a replacement for the install CDs."  No attempt is made to rescue data--it's a straight up wipe & OEM install.  The only difference is that the installation files are drawn from the 'recovery' partition and not CDs.
That's the worst kind of paternalism I've seen so far in connection with Windows... Pathetic. Apparently they assume that users are stupid. Well, nothing I worry much about anymore. This is sick.

Yes, I think you should be able to free up the space by deleting the partition and resize the remaining ones. The harddisk is simply a harddisk after all. Harddisks are not made for Windows only so I don't think this will create any issue. Use either PartitionMagic (Windows) or the Ubuntu Live CD (GParted).

---

