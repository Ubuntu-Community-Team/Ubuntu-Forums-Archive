---
title: "I just installed ubuntu (dual booting with windows xp)"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-08
I have windows xp pro installed on my primary hd and ubuntu installed on a slave drive , how do I edit the boot list thing so I just can choose from ubuntu and xp within 5 seconds and let xp boot up automatically if nothing is picked. I also want to know how I can speed up the boot up for ubuntu, it takes about 3min or more and how comes I cant see the slave drive that has ubuntu in win xp pro

p3 866mhz, 512ram, 20gb hd w/ 2 partitions, 8gb(slave), ati 9000 64mb

---

### Post by drizek on 2005-08-08
[QUOTE=Tristan9669]I have windows xp pro installed on my primary hd and ubuntu installed on a slave drive , how do I edit the boot list thing so I just can choose from ubuntu and xp within 5 seconds and let xp boot up automatically if nothing is picked. I also want to know how I can speed up the boot up for ubuntu, it takes about 3min or more and how comes I cant see the slave drive that has ubuntu in win xp pro

p3 866mhz, 512ram, 20gb hd w/ 2 partitions, 8gb(slave), ati 9000 64mb[/QUOTE]
 the reason why you cant see the ubuntu drive in windows is because windows doesnt support reiserfs/ext3. there are tools you can download for iwndows which let you browse linux partitions though. try googling one for your filesystem type.

---

### Post by aysiu on 2005-08-08
[QUOTE=Tristan9669]I have windows xp pro installed on my primary hd and ubuntu installed on a slave drive , how do I edit the boot list thing so I just can choose from ubuntu and xp within 5 seconds and let xp boot up automatically if nothing is picked.[/QUOTE]
[i]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst[/i]

Change default 0 to default 1
Change timeout 15 (or whatever it is) to timeout 5

Save.

---

### Post by Tristan9669 on 2005-08-09
[QUOTE=aysiu][i]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst[/i]

Change default 0 to default 1
Change timeout 15 (or whatever it is) to timeout 5

Save.[/QUOTE]
this didnt work, its still the same

---

### Post by aysiu on 2005-08-09
[QUOTE=Tristan9669]this didnt work, its still the same[/QUOTE]
Can you post your /boot/grub/menu.lst?

I think I forgot that Ubuntu makes three different Ubuntus before it get to XP.
So default should be 3, not 1. 0 means the first entry, 1 the second, 2 the third, 3 the fourth. If Windows is the fourth entry, default should be 3.

Still, please post your /boot/grub/menu.lst

---

### Post by Tristan9669 on 2005-08-09
[QUOTE=aysiu]Can you post your /boot/grub/menu.lst?

I think I forgot that Ubuntu makes three different Ubuntus before it get to XP.
So default should be 3, not 1. 0 means the first entry, 1 the second, 2 the third, 3 the fourth. If Windows is the fourth entry, default should be 3.

Still, please post your /boot/grub/menu.lst[/QUOTE]
wtf after i changed it, I cant boot up to any thing not ubuntu or xp, how do I change it back to the way it was, my computer just hangs at the part right before the boot list shows

---

### Post by aysiu on 2005-08-09
Was Windows XP, in fact, your fourth entry? If you didn't have a fourth entry, you can't use the fourth as the default.

Okay. For now, though, you just need to set things right. Can you control-alt-F1 or control-alt-F2? Do either of these get you to a command-prompt? Do you have the Ubuntu live CD or any Linux live CD available?

---

### Post by Tristan9669 on 2005-08-09
i have the Ubuntu live CD

---

### Post by aysiu on 2005-08-09
Boot the live CD. Do you know how to mount partitions? My guess (though, you should double-check) is that your Ubuntu slave drive is /dev/hdb1. If that's the case (again, double-check this), you should

[i]sudo mkdir /ubuntu
*sudo mount /dev/hdb1 /ubuntu *

Then

*gksudo nautilus* (probably the easiest way to do this), and browse to /ubuntu/boot/grub/menu.lst and replace the new one with the old backup copy.

---

### Post by Tristan9669 on 2005-08-09
I put in the install cd and went to the parttion section (didnt do anything) and then restart the computer and everything came back to normal with 5 seconds to choose os, but it still loads up ubuntu first instead of xp

---

### Post by Lord Illidan on 2005-08-09
Show us your /boot/grub/menu.lst

About the seeing ubuntu drive in Win XP, there is a good program out there..
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

### Post by aysiu on 2005-08-09
Seriously. If you post your /boot/grub/menu.lst, we can help you out a lot more.

---

### Post by Tristan9669 on 2005-08-09
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
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
I want to have like 2 seconds to choose just between xp and ubuntu with xp first in order and ubuntu second

---

### Post by aysiu on 2005-08-09
[QUOTE=Tristan9669]
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
[/quote]
Okay, this **default 0** refers to the 1st entry being the default booting one. Now, I noticed that there are the words "title" and "root" associated with "other operating systems." So, I'm not sure if changing default 0 to default 3 will work. Your best bet is to cut and paste the Windows entry in front of the Ubuntu ones. That way, you'll be absolutely certain it's the 1st (or 0th entry).
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

This is easy. Change this from timeout 10 to timeout 2.

> 
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
 Each of these is an entry. This is the first entry (0).

> 
title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
 This is the second entry (1).

> 
title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot This is the third entry (2).

> 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
 This is the part I'm uncertain about. Is this the fourth entry (3)? I don't know. That's why I suggested that, rather than messing with the default #, you just cut and paste Windows to be in front of the first Ubuntu entry.

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
 So cut and paste this part and put it in front of the first entry.

In other words, your /boot/grub/menu.lst should look like this:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


```

---

### Post by Tristan9669 on 2005-08-09
Yeah I was confused about that also 3 or 4 but I'll just move it up like u said, thanks

---

### Post by aysiu on 2005-08-09
[QUOTE=Tristan9669]Yeah I was confused about that also 3 or 4 but I'll just move it up like u said, thanks[/QUOTE] Please confirm that it works. I felt terribly after you were unable to boot last time.

---

### Post by Tristan9669 on 2005-08-09
Ok everything worked out  :grin: , I decided to let ubuntu be default and to run automatically and have xp on the second line and the timeout 2 seconds

---

### Post by aysiu on 2005-08-09
Phew. I was kicking myself, "Damn it. You screwed up somebody's boot configuration." Glad it all worked out.

---

### Post by PeP on 2005-08-09
[QUOTE=Tristan9669]Ok everything worked out  :grin: , I decided to let ubuntu be default and to run automatically and have xp on the second line and the timeout 2 seconds[/QUOTE]
well you should bring back XP to be the first or the last entry OUT OF THE AUTOMATIC CONFIG SECTION where all the linux entries are

when you run update-grub (each time you install a new linux-image) it will mess with this part.

then if you want ubuntu as a default change the default to 1 (and keep it as a low value so that you can remove kernel-image without going down that figure)

---

### Post by aysiu on 2005-08-09
Thanks for the P.S. I only half know what I'm talking about--being a three-month newbie myself.

---

