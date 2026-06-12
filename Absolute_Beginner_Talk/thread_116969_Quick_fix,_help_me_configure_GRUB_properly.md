---
title: "Quick fix, help me configure GRUB properly"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by sesstreets on 2006-01-13
Im not sure how to do this, so i thought i would just ask out right. I just installed ubuntu TODAY! on my dell 80gb monster lol

I used partition magic to cut out 20 gb of the 80 and make it fat32, so then i booted the install disk (THAT THEY SENT ME =O) told it to format the fat32 partition as ext3 i belive, anyway.

I had winxp home before and now when my computer turns on, I want the default to be windows xp instead of ubuntu (for my parents :P)

Ive seen similar boot questions so here is my boot.lst thingy:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



I wasnt sure what part u guys wanted so i just posted the whole thing.

---

### Post by jimrz on 2006-01-13
[**[COLOR="Sienna"]this[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=116706&highlight=boot+order") should about cover it.

---

### Post by sesstreets on 2006-01-13
*smacks head*

---

### Post by sesstreets on 2006-01-13
Wait...it doesnt...can someone just change it so that windows is the default, then ubuntu, then recover, then that memtest thing?

---

### Post by Mustard on 2006-01-13
Going on the thread mentioned above, I would try changing 'default' to '5'.

What did you change it to?

I just counted down your list of entries starting the count at zero.  So I'm hopeful that I am close. :)

It might even be '6'.

---

### Post by sesstreets on 2006-01-14
nope...COMEON how hard is it to edit that file and give it back to me...i tried it 4 times!

---

### Post by ned.b on 2006-01-14
I have modified your script by changing default from 0 to 6.  Prior to this change our menu.lst files were the same and I have tested this menu on my system.  I recommend that you make a copy of your old file before you make ANY changes though!

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

NB I think that when there is an update to this grub menu and a new option is added you will need to change the 6 to a 7 or delete/comment one of the old options - just something to bear in mind.



# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot

title Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd /boot/initrd.img-2.6.12-10-386
boot

title Ubuntu, kernel 2.6.12-9-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by sesstreets on 2006-01-14
[FONT="Impact"]**[SIZE="7"]MUCH THANKS![/SIZE]**[/FONT]

---

### Post by ned.b on 2006-01-14
[QUOTE=sesstreets][FONT="Impact"]**[SIZE="7"]MUCH THANKS![/SIZE]**[/FONT][/QUOTE]

[FONT="Impact"]**[SIZE="7"]MUCH WELCOME![/SIZE]**[/FONT] :)

---

