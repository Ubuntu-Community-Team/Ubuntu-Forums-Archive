---
title: "I probably missed something on install?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Jestocost on 2008-02-28
Bear with me, here's the situation: successfully installed Ubuntu on external USB HD, leaving internal HD with Vista perfectly safe. Everything works fine in both OS, but if the external HD isn't plugged in the machine will not boot (and hence Vista is inaccessible) to any of them both.

Did I miss something during the install process that I should have done different? Can I fix this so I can boot without the external USB, preserving everything both Ubuntu and Vista that already exists and being able to run them both from a GRUB screen? I see there's this tool called Super Grub Disk. Is it safe to use it to achieve what I need? (I do have backups of everything, but it would be bothersome to have to do a reinstall of Ubuntu and/or Vista to solve this.) Feel free to also explain to me how to avoid falling into a similar situation if I ever do another external HD installation of Ubuntu.

Thanks in advance for your help.

---

### Post by skymera on 2008-02-28
The boot file is on your Ubuntu install, which is the USB HD.

so if it isn't plugged in the bootloader dosent exist and your PC dosent boot.

You can try and make the windows bootloader default and just add your Ubuntu install to it.

---

### Post by Jestocost on 2008-02-28
Thanks, that explains the problem.

Now, and sorry for my denseness, how do you make a windows bootloader the default and still being able to dual boot both OS?

---

### Post by skymera on 2008-02-28
o ermm, i forgot now.

when i did it a year ago i did a short google search, i would do it now and post a link but im in a hurry :( sorry.

hope you get it all sorted

---

### Post by jan quark on 2008-02-28
please post the out of

```
cat /boot/grub/menu.lst
```

---

### Post by Jestocost on 2008-02-28
Here it goes...

> [FONT="Courier New"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout         15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=b971976f-7243-4db7-83ff-1cdaa6101ee3 ro

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
# defoptions=splash vga=792

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b971976f-7243-4db7-83ff-1cdaa6101ee3 ro splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b971976f-7243-4db7-83ff-1cdaa6101ee3 ro single
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
[/FONT]

---

### Post by jan quark on 2008-02-28
make a backup of your menu.list

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

and then run
```

gksudo gedit /boot/grub/menu.lst
```

and change 

```
default 0
```
to
```
default 4
```

---

### Post by Xarok on 2008-02-28
Yeah I'm having a similar problem,

I had two hardrives in a comp, one with windows and one blank.
I slected the blank one for install, but aparently it installed Grub on the windows disc anyways without asking me.

I believe the only way to get it off the Windows disc is to erase the entire disc, but I can't do that because I have no back-up CD to re-install windows.

What I wanted to do was just select the boot disc with the BIOS, But I can't do that now. and I always have the dumb grub load up!

Piece of SH1T!

---

### Post by Jestocost on 2008-02-28
jan quark, won't that just change the default selection for the GRUB menu? Just judging from the comments on the output up there, feel free to smack me if I'm talking nonsense.

What I need is apparently (as skymera said) to replace the internal HD's bootloader by a full one, apparently from Windows...

I found something called EasyBCD through Google, I think I will give it a try and report back.

---

### Post by hyper_ch on 2008-02-28
the "easiest" thing would to be setup your /boot partition on your (windows) harddisk. You'd have to create a 200 MB (or so).

---

### Post by Jestocost on 2008-02-28
Well, that was instructive. Heh. EasyBCD happily installed a new bootloader (and a lovely one!) and I can boot Vista without the external HDD. But now Ubuntu doesn't work anymore. Some browsing through the EasyBCD forums tells me this was probably unavoidable, due to some limitations of the GRUB setup process during Ubuntu install. Their words, I have no clue here. They do seem to offer a guide to tweaking that setup process so as to avoid the kind of problem I had. I might give it a try when I have time to reinstall Ubuntu to the external USB drive.

---

### Post by eldepeche on 2008-02-28
What I think you did (knowingly or not :)):

Installed Grub to the internal drive's Master Boot Record (MBR), telling it to look for configuration information on the external drive. The MBR is quite small and cannot hold all the information that Grub needs. Grub then writes in the MBR, "Look at this file (grub.lst) for configuration information." If Grub can't find that file (because, for instance, it exists on an external drive) then it spits out an error.

What I would do:

Boot from the Ubuntu live CD and use Gparted to shrink and move the NTFS Vista partition to make room for a small (100 MB) partition with the ext2 filesystem. Then reinstall Ubuntu to the external drive, but in the partitioning stage, tell it to use the new partition as /boot . This will cause the Grub configuration to be written to the new partition on the internal drive (as well as installing the kernel images there). Then when you boot the computer, Grub will look for its configuration information on the internal drive. 

There are other options as well.

---

### Post by ajgreeny on 2008-02-28
I don't know if Vista is the same as XP, but the problem there is dead simple to sort out.
You need to boot into the Ubuntu live CD, and follow the info below, except towards the end you need to make sure you put grub onto the external disk.

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc (from the **sudo fdisk -l** command) as appropriate.  This is where you will need to set your external hard disk as the grub recipient.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

In your BIOS you then set the first boot disk as your external disk, and you can find that with ```
sudo fdisk -l
``` in the live disk terminal.  You will need to restore the windows MBR to the windows hard disk, but I'm not sure how to do it in Vista, and set the hard disk with windows as the second boot device in BIOS.  Now when you boot up with the external disk attached it will boot into grub, and you will be able to chose which OS to use.  When the external disk is not attached, however, the system will look for first boot device then go to second boot device and boot to the windows MBR.

---

