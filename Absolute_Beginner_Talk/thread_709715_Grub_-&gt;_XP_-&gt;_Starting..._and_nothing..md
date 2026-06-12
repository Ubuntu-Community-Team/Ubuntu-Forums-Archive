---
title: "Grub -&gt; XP -&gt; Starting... and nothing."
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-27
Ok, I have made multiple posts and private messages just trying to get this to work. I have been working on this thing for 3 days now, when i have time of course, and have been unsuccessful. I don't want to say o well windows it is, cuz i really want to experience the environment of Ubuntu.

My questions have not been answered with a clear cut solution yet.

I get starting... when i boot xp, like so many others have. I went to teh windows rescue cd and typed fixmbr, and fixboot, no grub menu now. Used ubuntu live cd to restore the grub menu using:

sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
quit

I now have grub menu again, hit XP and i get starting...

PLEASE someone come up with something. I know i'm not the only one =( I have been searching and searching and reading write ups upon write ups

-Justin Thanks in advance

---

### Post by Presto123 on 2008-02-27
It looks like your fixing one, and then deleting out the other when you do that. I may be wrong. I think you would be good to download the SuperGrub LiveCD and use their utility to boot from the "Linux+Windows" MBR file.

It's pretty simple to use and will help while you wait for an answer on how to edit Grub.

---

### Post by jw5801 on 2008-02-27
Can you post your /boot/grub/menu.lst file? My section for Windows looks like this:
```
title           Microsoft Windows XP
root            (hd0,1)
makeactive
chainloader     +1
```
The important bits are the "makeactive" and "chainloader +1" as these fool Windows into thinking it's the only thing on the disk, otherwise it'll have issues booting.

---

### Post by Victormd on 2008-02-27
That can be related I think mainly to the line "chainloader +1" - I removed this line once just to see what would happen and my windows stoped booting. I didn't know that the "makeactive" option would affect windows' boot (tkx for the heads up jw5801). None the less, check your menu.lst file and if possible, post it here so we can take a closer look.

---

### Post by HoLLyw00dGT on 2008-02-27
SOrry still new with terminal, i copied /boot/grub/menu.lst and it said permission denied, then tried sudo /boot/grub/menu.lst password: then it said command not found. How do i type the command:oops:

---

### Post by Duck2006 on 2008-02-27
To look at your menu.lst type, and post the output here.

cat /boot/grub/menu.lst

and post the output of

sudo fdisk -l

---

### Post by dstew on 2008-02-27
> tried sudo /boot/grub/menu.lst password: then it said command not found. That is because /boot/grub/menu.lst is really not a command, it is the name of a text file. To see the file, use **cat** /boot/grub/menu.lst as Duck2006 says.

---

### Post by HoLLyw00dGT on 2008-02-27
Here's what i got:

justin@justin-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=57736b91-3bba-4541-8dfd-28164bc9c0b7 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=57736b91-3bba-4541-8dfd-28164bc9c0b7 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=57736b91-3bba-4541-8dfd-28164bc9c0b7 ro single
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
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

justin@justin-desktop:~$

---

### Post by HoLLyw00dGT on 2008-02-27
I see all of these success stories. I just can't seem to get it right.

---

### Post by Trouncing on 2008-02-28
Okay. I started off with Windows Vista on the current computer that I am on now. I tried to install Ubuntu onto the hard drive, which was completely wiped and reformatted to ext3 and swap format for this purpose. Everything seems to have installed correctly, but when I restart the computer, it doesn't boot up. The hard drive LED indicator on my computer blinks on and off for a matter of seconds, and then stops.. I end up with a black, blank, screen with no Ubuntu login. If I'm not mistaken, it was kinda like the following error:

[ 0.668000] PCI: Cannot allocate resource region 1 of device 0000:00:14.0.

Except I think it was in Region 5 instead of 1. I have no clue on how to correct this problem. I went to the site where I got the error from above, and it said that it could possibly be a BIOS issue, but the BIOS on this computer was installed on October 07, so I don't think they would have another version of it out quite yet. Please, anyone, let me know how to fix this. I'm trying to get this computer based back onto Linux, but I've never tried using Ubuntu before, and I'm clueless as to how this system works.

If you do need my specs, they are:

Dell Inspiron 1521 Laptop
120GB Western Digital SATA HD
1918MB AMD Turion64 x2 RAM

ANY information would be EXTREMELY helpful. Thanks :)

---

### Post by lunar71 on 2008-02-28
OK, where is the output from the command:
sudo fdisk -l

---

### Post by HoLLyw00dGT on 2008-02-28
after my manual partitioning last night...

justin@justin-desktop:~$ sudo fdisk -l
[sudo] password for justin:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System
/dev/sda1 * 1 24316 195318238+ 7 HPFS/NTFS
/dev/sda2 24317 27963 29294527+ 83 Linux
/dev/sda3 27964 28474 4104607+ 5 Extended
/dev/sda5 27964 28474 4104576 82 Linux swap / Solaris
justin@justin-desktop:~$

---

### Post by Duck2006 on 2008-02-28
This is the lines i have to boot windoze.

#title          Windows XP
root           (hd0,0)
savedefault
chainloader    +1

I have no makeactive, because the flag is set on the win partition. You could try that.

---

### Post by Victormd on 2008-02-28
> **Trouncing said:**
> 
If you do need my specs, they are:

Dell Inspiron 1521 Laptop
120GB Western Digital SATA HD
1918MB AMD Turion64 x2 RAM

What's your graphics card?
I had a similar issue installing on an HP dv6000 series, Turion 64X2 and nvidia graphics card.

I had to add "noapic" at the end of the kernel line in the grub menu. You can try this by hitting "e" at the grub menu, and at the kernel line, hit "e" again to edit that line. The cursor will already be at the end so just add "noapic" (without quotes) and see what that does for you. Please keep in mind that you might have to manually add this to the menu.lst file.  In my case, after I was able to boot and download all the updates, the problem was solved.

I ask about your graphics card because I also had an issue where I had to add this (option "nvagp" "2") to my xorg.conf file at the end of the "device" section otherwise, ubuntu would just hang.

Hope this helps.

---

