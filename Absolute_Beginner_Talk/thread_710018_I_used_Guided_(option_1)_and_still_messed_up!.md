---
title: "I used Guided (option 1) and still messed up!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-28
I used the freakin GUIDED partitioner when installing this time and rebooted, linux works, windows is "starting..." I mean i used teh GUIDED one...wtf! >_< i cant take this anymore. I just want to dual boot successfully...FOR ONCE!


Justin

ps. this is part rant/part a plea for help i guess

---

### Post by Fred_E _krugar on 2008-02-28
LOL  you sound like me. Exactly. But here is the easyiest way to do this: [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) ,Just print that article.

---

### Post by HoLLyw00dGT on 2008-02-28
You don't understand lol, that write up, although its not for 7.10, is the exact way i did it, moved the slider, and isntalled, very simple. Am i supposed to click the advanced button and change something?

---

### Post by apothecaryaaron on 2008-02-28
I'm not an expert by any means, but I've got two systems dual-booting, so I'll try to help. What are you trying to dual-boot? Are you starting clean, or with one installed already? 
 
As one quick answer, I've always used manual for install. I felt safer that way.
 
EDIT:  If its XP, what does your /boot/grub/menu.lst look like?  XP is picky, and windows "Starting..." sounds like you may have installed fine, but just need to do some rootnoverify type of magic.

---

### Post by JoshuaRL on 2008-02-28
No, it should do it's thing for you.  What issues are you having?

---

### Post by HoLLyw00dGT on 2008-02-28
I start with a restored version of XP (absolutely nothing on it, just plain xp from when i built my comp 3 weeks ago) defrag not that i really need 2, nothing on it. Then follow guided (ive tried manual, same issue) move teh slider to the right a little bit, install, reboot, linux works (7.10) windows just says starting...

I have not been successful over the last 3 days but i'm not one to give up.

If you think i should manually do it then i will, just need to know how to properly do it. i'm at a fresh install of xp now....for the 2938473 time.

---

### Post by apothecaryaaron on 2008-02-28
Nah, manually is a personal preference, I believe.  Makes me feel more in control.  
 
From my XP experience, it sounds like you are doing it correctly, we just need to tweak your grub so that XP thinks that it is the primary OS.  Mine ended up requiring additions to the menu.lst, and it suddenly worked.

---

### Post by HoLLyw00dGT on 2008-02-28
Is there an easy detailed way to do that? I have supergrubCD, or i heard you can do that using ubunu live cd as well...i just want it done so i can go 2 bed haha

---

### Post by apothecaryaaron on 2008-02-28
Post the contents of the menu.lst file and I'll see if I can find the links I used.
 
```
gksudo gedit /boot/grub/menu.lst
```
 
I'm at work (posting instead of working:)) so I don't have anything bookmarked.

---

### Post by angry_johnnie on 2008-02-28
If memory serves, the first option is to resize Windows, isn't it?   did you defrag first?  And also, how did you resize it?  When you move the slide bar and choose the new size, it's not the size of your Linux partition you're changing.  It's windows.  Did you, by any chance, make it too small?

---

### Post by apothecaryaaron on 2008-02-28
If your menu.lst is the same as it was in the [other post]("http://ubuntuforums.org/showthread.php?t=709715"), try changing it to this:
 
```
 
title Windows XP
root (hd0,0)
rootnoverify (hd0,0)
makeactive
chainloader +1

```
 
Notice the rootnoverify line, that was the fix for me.

---

### Post by HoLLyw00dGT on 2008-02-28
Here it is:

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
# kopt=root=UUID=34097540-5ea7-45cb-8b0b-1c483aaf70d7 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=34097540-5ea7-45cb-8b0b-1c483aaf70d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=34097540-5ea7-45cb-8b0b-1c483aaf70d7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Yea, i defragged, and nah, i didn't make it 2 small. one thing i did right lol

EDIT* so make:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +


into:
title Windows XP
root (hd0,0)
rootnoverify (hd0,0)
makeactive
chainloader +

?

---

### Post by apothecaryaaron on 2008-02-28
You can keep the **savedefault** if you would like, and the **title** line is just preference (that was what was used in my reference thread), and make sure that the chainloader line is **chainloader +*1***
 
That may not be an instant fix, but for me it was all I needed.

---

### Post by HoLLyw00dGT on 2008-02-28
Yea it is, just didn't grab the 1. So keep saveddefault, but PUT rootnoverify (hd0,0) after saved default...and hit enter? sorry for the tedious questions, i'm new to the terminal

---

### Post by Sturmeh on 2008-02-28
Sadly the guided installs all suck for me, so I use manual, and having it explained to me once was enough.

You need to make 2 partitions at minimum, one logical and one primary.

SWAP should be 1-2x the size of your ram, and should be logical.
/ should be as big as you want it, but no smaller than say 4GB. PRIMARY!

Then just install it!

---

### Post by HoLLyw00dGT on 2008-02-28
Well, i'm pretty sure i was making the linux swap a primary as well, NOT logical, that might have been it lol. I'm going ot see if this works, if not, i'll try another manual tomorrow i guess =(

---

### Post by apothecaryaaron on 2008-02-28
title Microsoft Windows XP Professional
root (hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
 
That would be the order I used.  What are you using to edit it?  gedit was easiest for me, being an old Windows guy, it works like notepad.  Open it with ```
gksudo gedit /boot/grub/menu.lst
``` edit it, save, and close.
 
Once it's saved, reboot and try out XP, then come back and we'll see if it's fixed or needs more research.

---

### Post by HoLLyw00dGT on 2008-02-28
Starting...


Nothing man. Nothing.

---

### Post by apothecaryaaron on 2008-02-28
Hmmm.  OK.  That's not what I wanted to hear.  I'm not sure what else to do, that has not failed me before.
 
I'm afraid that something may have still gotten messed up with XP.  I have seen someone build their partitions BEFORE installing XP, install XP to its spot, then install Ubuntu, swap, etc to their spots, but I hate to tell someone to fresh install.  If this isn't a time critical thing, I'd sleep on it and wait for the more experienced users to read this thread.
 
Anyone else have anything?

---

### Post by HoLLyw00dGT on 2008-02-28
Anything would be great, i'll check in the morning if I have time, if not, tomorrow evening. I feel as if i have tried everything.

justin@justin-desktop:~$ sudo fdisk -l
[sudo] password for justin:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24316   195318238+   7  HPFS/NTFS
/dev/sda2           24317       27963    29294527+  83  Linux
/dev/sda3           27964       28474     4104607+   5  Extended
/dev/sda5           27964       28474     4104576   82  Linux swap / Solaris
justin@justin-desktop:~$ 


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
# kopt=root=UUID=7830cb8b-60a1-4960-9c4f-916190fd2f2c ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7830cb8b-60a1-4960-9c4f-916190fd2f2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7830cb8b-60a1-4960-9c4f-916190fd2f2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by HoLLyw00dGT on 2008-02-28
Shameless BUMP

Tried manual installing, same thing, xp wont boot, i can see the XP partition when i'm in linux and see my files, but can't load it, so i'm assuming my MBR is ****** up, althought IDK how to NOT **** it up.

---

### Post by HoLLyw00dGT on 2008-02-28
Shameless bump, write ups not working, still having problems. Bout to say eff linux and stick with windows completely.

---

### Post by apothecaryaaron on 2008-02-29
I got broke out my test system and I got this to work.  It uses the XP bootloader instead of grub.
 
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

