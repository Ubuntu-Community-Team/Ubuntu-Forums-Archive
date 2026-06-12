---
title: "Windows not booting from Grub"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ASTP001 on 2007-06-17
What's the problem? Why can't I boot windows XP from the grub boot loader?

---

### Post by jonward0690 on 2007-06-17
Does windows show up in tho grub menu,can you give us more details about the problem.

---

### Post by Malibu Illusion on 2007-06-17
Issue:

```
cat /boot/grub/menu.lst
```

Post the output.

---

### Post by ASTP001 on 2007-06-17
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
# kopt=root=UUID=58f64588-bc9f-4690-8e3c-fa3cae66f29d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=58f64588-bc9f-4690-8e3c-fa3cae66f29d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=58f64588-bc9f-4690-8e3c-fa3cae66f29d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Malibu Illusion on 2007-06-17
Looks like you've got two Windows operating systems appearing on the GRUB list, mount points hd0,0 and hd0,1.  What error messages, if any, are you receiving after attempting to start up the Windows XP installation?  If that file is anything to go by, GRUB should be correctly forwarding you to the OS; the problem may be with the other operating system's installation itself, unless those file roots are wrong which, at first glance, doesn't appear to be the case.

---

### Post by ASTP001 on 2007-06-17
Well, the second one where it says Windows NT/2000/XP is actually a recovery thing... I don't think that's really a OS, and when I try to boot XP Mdeia center It says "Starting up..." But nothing happens, I waited for about 10 minutes...

---

### Post by Malibu Illusion on 2007-06-17
You could try changing the stanza in /boot/grub/menu.lst for XP to:

```
title Windows XP Media Center Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

And seeing if that helps.  If not, posting the output of this will help in examining your structure:

```
sudo fdisk -l
```

---

### Post by ASTP001 on 2007-06-17
I'm going to post that just incase that doesn't work since I'll need to restart the comp...

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21728   174530128+   7  HPFS/NTFS
/dev/sda2           29259       30401     9177840    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           21729       25262    28386855   83  Linux
/dev/sda4           25263       29258    32097870    5  Extended
/dev/sda5           28946       29258     2514141   82  Linux swap / Solaris
/dev/sda6           25263       28787    28314499+  83  Linux
/dev/sda7           28788       28945     1269103+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by ASTP001 on 2007-06-17
The noverify thing.. It didn't  work. :(

---

### Post by Malibu Illusion on 2007-06-17
WinXP seems to like being on the first partition of the first drive...it is in the case so no mapping is required also the GRUB list is referencing the correct location so there's not a problem there.  Hmm.  Me personally, I cannot see why it is not booting unless it's a Windows issue itself.

Interested in hearing from anyone else with a similar issue that was able to solve it through GRUB configurations.  For me personally, I don't see why it's not booting from a GRUB perspective.  You've posted everything that'll assist someone else in solving this though if I've overlooked something.

---

### Post by ASTP001 on 2007-06-17
Maybe I should wait longer... or something's wrong with the OS itself...

---

### Post by ASTP001 on 2007-06-17
So uh... can anyone help me???

---

### Post by Dedoimedo on 2007-06-17
Hello

Grub will get confused if there is more than one instance of Windows on the same hard disk. You need to use the hide and unhide method:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
chainloader +1
makeactive

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows NT/2000/XP
unhide(hd0,1)
hide(hd0,0)
rootnoverify (hd0,1)
chainloader + 1
makeactive

Try this, see if it works.
Dedoimedo

---

### Post by ASTP001 on 2007-06-17
Okay, I'm going to try that out right now.

---

### Post by ASTP001 on 2007-06-17
Nope didn't make any difference... still says "Starting up ..." But nothing happens... Uh... Maybe I'm missing some files needed to boot XP....:S

---

### Post by Dedoimedo on 2007-06-17
Hello,
Strange. Did Windows boot before you installed Ubuntu?
Would you consider repairing MBR then reinstalling GRUB?
Dedoimedo

---

### Post by ASTP001 on 2007-06-17
Yes, it worked before installing linux... How would I repair MBR?

---

### Post by ASTP001 on 2007-06-17
Help anyone?:S

---

### Post by confused57 on 2007-06-17
> **ASTP001 said:**
> Yes, it worked before installing linux... How would I repair MBR?

Here are several ways to restore your Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk is also capable of restoring your mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by ASTP001 on 2007-06-17
It says "Windows XP 'Recovery Console'
Just put in your Windows XP install CD, and boot into the recovery console and use the so-called 'FIXMBR' command."

Well, the CD doesn't even boot up for some reason......

---

### Post by ASTP001 on 2007-06-17
And as for MbrFix.exe method... I can't write anything to the C drive... it says you do not have permission to write to that folder...

---

### Post by ASTP001 on 2007-06-17
So how will I be able to write in the C drive...?

---

### Post by confused57 on 2007-06-17
> **ASTP001 said:**
> And as for MbrFix.exe method... I can't write anything to the C drive... it says you do not have permission to write to that folder...

If you're able to boot into Ubuntu, your best bet would be to burn a copy of the Super Grub Disk.  I think MbrFix will only work if you're able to boot into Windows from grub.

---

### Post by ASTP001 on 2007-06-17
okay, I'm downloading it... sgd_current.iso

---

### Post by ASTP001 on 2007-06-17
Okay, the super grub disk starts up, then I dunno what to do....

---

### Post by confused57 on 2007-06-17
> **ASTP001 said:**
> Okay, the super grub disk starts up, then I dunno what to do....

I think you select:
1.)English
2.)Windows
3.)Fix Windows Boot

This "should" restore Window's IPL to the mbr.

---

### Post by ASTP001 on 2007-06-17
then it'll boot XP right there? or do I have to take the CD out and try to boot XP again?

---

### Post by ASTP001 on 2007-06-17
Okay, I tried that and it said I need to uninstall grub from a partition or something, so I selected the windows partition... But nothing happened... what should I do??

---

### Post by confused57 on 2007-06-18
> **ASTP001 said:**
> Okay, I tried that and it said I need to uninstall grub from a partition or something, so I selected the windows partition... But nothing happened... what should I do??

If you did "Fix Boot of Windows", removed the SGD & Windows would still not boot...I'm not sure what the warning was about uninstalling grub, unless you possibly installed grub to your Window's partition.

Try to Boot Windows from SGD.

If you did happen to install grub to your Window's partition, you'll just about have to find a Window's install cd, enter recover console by pressing "r", then running the commands FIXBOOT & FIXMBR.

Hopefully, SGD will be able to boot your Windows.

---

### Post by ASTP001 on 2007-06-18
Hmm, the windows installation CD doesn't boot for some reason. =\ I'm going to try all that again... lol how many times I've rebooted my computer in the past few hours.... x.x

---

### Post by ASTP001 on 2007-06-18
now it says unable to detect file systems...:(

---

