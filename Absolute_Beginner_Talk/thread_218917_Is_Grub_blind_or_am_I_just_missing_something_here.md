---
title: "Is Grub blind or am I just missing something here?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by SkyNet2029 on 2006-07-19
First, sorry about the long post.
I can't seem to get Grub to see my Edubuntu partition anymore. Here is what I did on my machine, in order of operation.
1. Installed Windows Server 2003 Enterprise Edition.
This is located on its own device (/dev/hda1) and occupies the entire device. (hd0,0) in Grub
2. Installed Edubuntu 5.10 on first partition of second HDD. 
**For some reason Grub cannot see this partition.Should be (hd1,1) in Grub
3. Installed Kubuntu 6.06 on Second Partition of Second HDD.
(hd1,2) in Grub
All was well and I was able to boot successfully into Windows after installing Edubuntu. Now that I have installed Kubuntu, I can only boot into that. Although my grub boot menu does give me the option to boot into Windows, if I select that, it just sits (it does not hang as the progress indicator on bootsplash keeps moving) there at the bootsplash. Safe mode is a no-go as well.
grub does not show my Edubuntu partition as a bootable option. 
I can manually add the entry, (which refuses to boot and errors out with an error 21 (item not found) but once I do an 'update-grub', my manual corrections to the menu.lst go away.
I am at a loss as to what I can do and why grub cannot find my Edubuntu partition, since I can go into it directly if I open it as a folder in Kubuntu.

I have to keep Edubuntu, since my 3 year old son's vocabulary has skyrocketed since introducing him to all of the nifty training resources available. Yes, I have to keep Windows (for now) since I am in process of writing a review of server-class operating systems and their (m)alloc of available resources when overly taxed.

Any help would be greatly appreciated.  
](*,)

---

### Post by shoot2kill on 2006-07-19
if edubuntu is installed on first partition, then it should be (hd1,0) and kubuntu should be (hd1,1)

post here your menu.lst from the boot/grub directory...

---

### Post by SkyNet2029 on 2006-07-19
This is the output of my /boot/grub/menu.lst
I ran an update-grub to be certain I am posting current info.
I thought the same thing on the (hd1,0 and 1,1) but grub does not list as such and that kind of put me off until I realized I have a fat32 (shared between win/Linux) on second partition of second HDD. Sorry about that. 

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
timeout		15

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
# kopt=root=/dev/hdb5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hdb5 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hdb5 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,2)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hdb5 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,2)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/hdb5 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Server 2003
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by PriceChild on 2006-07-19
If you use a boot partition on another disk to the windows partition... then you need to use a special grub entry to fool windows into thinking its still got it. For example, i use this:

```
title Windows XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by SkyNet2029 on 2006-07-19
Well, grub hated that change. (Error 27 Unknown command) and fails to boot Windows.
As to the Edubuntu partition though, I think I have the crux of that problem's creation; When I installed Kubuntu, I set things up so as to mount the Edubuntu partition in a folder of its own (  /edubuntu  ), my thinking being that I could just access it from both Linux OS's that way. I know this would not change much in way of convenience, but now that I have been spelunking through the man(8) pages for grub and info grub, I realize that this mapping sets up the Edubuntu (and thus its corresponding vmlinuz) on a partition other than /boot, which is the only place grub looks at when running update-grub.
Bummer. So, I suppose I need to find out how I am to make update-grub look in a non-default location to get Edubuntu listed and loadable. That should prove to be rather easy once I get my head on straight. (It's rather early here, I mean).

As for the Windows, I may have to reinstall completely, which I think should work easier in my multiple disk setup if I unplug all drives except for the hd0 where windows will reside for purposes of installation and then plug them all back in and run an update-grub from the Kubuntu installation. That way the NT-loader won't get too cornfused and just nuke all of my pretty partitioning.

This may just turn out to be a jumper config error on my part, although I cannot recall having changed them recently, as the Windows install CD now just hangs at 'setup is starting windows' when I try a Recovery Console boot to just rewrite the MBR on that partition. Fun. Fun. Fun.

---

### Post by SkyNet2029 on 2006-07-22
Nevermind, I had set the 'bootable' flags to NO boot in partitioner for Windows and Edubuntu partitions. Whoops.

---

### Post by zeusdo on 2006-07-22
Can someone tell me where to find the menu list in GRUB? By the way I need to find it while booted up in Windows.

---

### Post by richbarna on 2006-07-22
> **zeusdo said:**
> Can someone tell me where to find the menu list in GRUB? By the way I need to find it while booted up in Windows.

[FONT=monospace]It's in [/FONT]> /boot/grub/menu.lst 

To see it from windows you need to install ex2fs. 
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

