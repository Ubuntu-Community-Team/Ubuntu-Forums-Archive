---
title: "Adding to the boot menu...some clarification."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Kevin Jones on 2008-03-03
Hello all.
I have three operating systems. Only two of which appear on my grub menu.
This is the situation:
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

#SOME DELETED LINES BELONG HERE!

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75eba9de-889b-4619-be0d-ba94a72d8bbe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=75eba9de-889b-4619-be0d-ba94a72d8bbe ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

As you can see both windows and ubuntu appear on this grub loader.
I  have never edited a boot menu, and I am a little bit aprehensive. 
Suse  10.3 is on SDA 5 of my hard drive. (that would make it hd0.4)
Can any one tell me where to insert the information for the hd0.4 partition so that the  grub menu  recognizes it and shows it on the boot menu. Most of the tutorials show how to add windows OS. My concern is  where to add the lines for suse.10.3
(The  information was gotten from [http://jazzz1s.blogspot.com/2007/10/working-with-grub-menu.html](http://jazzz1s.blogspot.com/2007/10/working-with-grub-menu.html))

Thanks very much everyone.

Kevin

---

### Post by confused57 on 2008-03-03
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Try a configfile entry in your menu.lst to boot Suse:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

add a configfile entry at the very end of your menu.lst to boot Suse:
```
title  Suse on /dev/sda5
configfile (hd0,4)/boot/grub/menu.lst
```
quit & save

I don't know if Suse uses grub.conf instead of menu.lst...if it does:
```
title  Suse on /dev/sda5
configfile (hd0,4)/boot/grub/grub.conf
```

As long as you don't change anything else and just add the Suse entry to the very bottom of your menu.lst, you shouldn't have any problems.  You created a backup with the 2nd command above, if anything happens to go wrong.

---

### Post by 0vermind on 2008-03-04
My problem is getting NeoGrub to point to the right config file to boot Ubuntu from Vista Boot Loader.
The default NeoGrub menu.lst does:
set -find--root --ignore-floppies /boot/grub/menu.lst

but that wasn't working it gave me the message:
Rebuilt partition table with Microsoft-Compatible fdisk.

So will adding the above to NeoGrub menu.lst be effective for me?

---

