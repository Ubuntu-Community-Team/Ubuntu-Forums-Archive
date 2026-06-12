---
title: "[SOLVED] Grub error 15"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-12-29
I am sorry for bringing this up again. I have searched the forum for a solution but seem that my problem is not covered.

problem: I had win xp installed first; then ubuntu gutsy on extended partition. GRUB controlled the boot menu very well. For some reason I had to reinstall xp on the first partition. Kept Ubuntu untouched.
XP rewrote to MBR as expected. Now ofcourse I want to also use Ubuntu, but can't see it at all. So I looked around here to see if I could reinstall GRUB back to control boot menu. So I followed [these ]("http://ubuntuforums.org/showthread.php?t=224351")instructions to reinstall grub.

Now grub menu appears, but when i select Ubuntu from the menu, the next screen says: Grub Error 15: unable to find file.

Could someone point me in the right direction to get me back to Ubuntu.

Thanks

S

---

### Post by OldTimeTech on 2007-12-29
Download a win98se boot disk from [www.bootdisk.de](www.bootdisk.de). Boot up with it. AT the command prompt type:
fdisk /mbr

Reboot into Ubuntu recovery mode and reinstall grub in mbr.

---

### Post by shuttleworthwannabe on 2007-12-29
I have win XP disc; Can I do  **fixmbr** at the prompt? and then boot with live Ubuntu CD and reinstall grub?

---

### Post by meierfra on 2007-12-29
fixmbr is a step backward. You already have Grub  installed correctly.  You just need to edit "menu.lst". Give me a second for instructions.

---

### Post by meierfra on 2007-12-29
I need some information. Boot from the LiveCD.

Go to Places->Computer and double click the Ubuntu partition. (This mount your Ubuntu partition.)

Post the output of 

```
sudo fdisk -l
```

and

```
cat /media/disk/boot/grub/menu.lst
```

(all "l" are lower case L, not the number one)

---

### Post by shuttleworthwannabe on 2007-12-30
I got quite late last night, and my computer was just tired...I have an issue with heating on this laptop; each time I run live CD the fans just go beserk, and computer shuts down spontaneusly...I think my fans need some cleaning (not not sure how to do this)...

anyway I gave it a rest, and I will follow your instructions right away...give a couple of minutes.
regards,
S

---

### Post by shuttleworthwannabe on 2007-12-30
Thanks, Here is the output for both the commands in one code:
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x38343833

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4063    30716248+   7  HPFS/NTFS
/dev/sda2            4064       12920    66958920    f  W95 Ext'd (LBA)
/dev/sda3            8127       12920    36242608+   7  HPFS/NTFS
/dev/sda5   *        4064        5872    13671252   83  Linux
/dev/sda6            5872        7610    13141138+  83  Linux
/dev/sda7            7610        8126     3903763+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /media/UBUNTU/boot/grub/menu.lst
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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=6c5e65d7-ab42-4a4e-98c6-2cdc4e08db81 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c5e65d7-ab42-4a4e-98c6-2cdc4e08db81 ro quiet splash vga=791 reboot=b
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6c5e65d7-ab42-4a4e-98c6-2cdc4e08db81 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,6)
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

```

Much appreciated.

S

---

### Post by meierfra on 2007-12-30
Right now you are trying to boot from your swap space. So no surprise that  that  does not work. Well you have two different linux partition : sda5 and sda6. I'm assuming   sda5 is your root partition. sda5 is (hd0,4).

So mount the ubuntu partition as before. Open menu.lst via

```
gksudo gedit  /media/disk/boot/grub/menu.lst
```

Change

#groot (hd0,6)

to

#groot (hd0,4)

and  three times

root (hd0,6)

to 

root (hd0,4)

Save the file and reboot.


If sda6 is your root partition, use (hd0,5) in place of (hd0,4). If you don't know try them both.
Edit: Instead of "try them both" I should have said:  Look at the output of
```
sudo grub
find /boot/grub/menu.lst
quit

```

---

### Post by shuttleworthwannabe on 2007-12-30
Unfortunately, changing (hd0,6) to (hd0,4) gave me a
Grub error 17: partition not found

I am pretty sure (hd0,4) is my root, and (hd0,5) my home; but I will try (hd0,5) as root (I may have gotten the sequence wrong).

Will come back.

---

### Post by BrownCoal on 2007-12-30
This might help: [http://ubuntuforums.org/showpost.php?p=4039112&postcount=7](http://ubuntuforums.org/showpost.php?p=4039112&postcount=7)

---

### Post by meierfra on 2007-12-30
> I am pretty sure (hd0,4) is my root, and (hd0,5) my home; but I will try (hd0,5) as root (I may have gotten the sequence wrong).

Sorry, I must have been sleeping when I told  you to just try. This is probably to late, but 

```
sudo grub
find /boot/grub/menu.lst
quit
```

tells you  the correct numbers.

---

### Post by shuttleworthwannabe on 2007-12-30
Meierfa,

Thanks it was (hd0,5). I am in Ubuntu right now. Many thanks it worked.

---

