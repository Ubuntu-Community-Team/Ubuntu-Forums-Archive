---
title: "Dual boot with XP problem!"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Casgeroth on 2006-06-10
Hi all,
I'm a complete n00b to this stuff so please bear with me.
I've been an MS guy for years mostly out of habit and have read a lot of good stuff about Ubuntu, so I thought i'd give it a try and dual-boot it with XP on my laptop.

After running the CD and going through the installation all seemed ok.
I've got Windows XP installed on the primary partition with Ubuntu (ext3?) on the next partition and the Swap on the third.

After reading up a bit on how to further tweak the OS and maybe get a few more things working (like having a more suitable res for this 15.4" screen, and maybe getting sound working), I thought i'd go back to XP for a bit as I needed to do a few things.

So I go to reboot and select my Windows XP option from Grub.
It didn't seem to like this and showed me:
[B]Booting Windows XP Professional
root (hd0,0)
Filesystem type unknown, partition type 0x7
Savedefault
Makeactive
Chainloader +1[/B]

I Googled this error and it seems that a lot of people have had this problem, but no-one's had a fix that i've been able to find or understand thus far without resorting to reinstalling XP.
A few suggestions were to change *root* to *rootnoverify*, and to add *boot* on the line under "Chainloader +1".
It took me AAAAAAGES to figure out how to legitimately edit the menu.lst file, but I eventually did it by using *sudo gedit /boot/grub/menu.lst* from the Terminal.
I added these changes and tried it, but still no go.
It just sits there with a flashing cursor doing nothing.

Can someone please help me get back to XP?!

---

### Post by sherlock-holmes on 2006-06-10
[QUOTE=Casgeroth]Hi all,
I'm a complete n00b to this stuff so please bear with me.
I've been an MS guy for years mostly out of habit and have read a lot of good stuff about Ubuntu, so I thought i'd give it a try and dual-boot it with XP on my laptop.

After running the CD and going through the installation all seemed ok.
I've got Windows XP installed on the primary partition with Ubuntu (ext3?) on the next partition and the Swap on the third.

After reading up a bit on how to further tweak the OS and maybe get a few more things working (like having a more suitable res for this 15.4" screen, and maybe getting sound working), I thought i'd go back to XP for a bit as I needed to do a few things.

So I go to reboot and select my Windows XP option from Grub.
It didn't seem to like this and showed me:
[B]Booting Windows XP Professional
root (hd0,0)
Filesystem type unknown, partition type 0x7
Savedefault
Makeactive
Chainloader +1[/B]

I Googled this error and it seems that a lot of people have had this problem, but no-one's had a fix that i've been able to find or understand thus far without resorting to reinstalling XP.
A few suggestions were to change *root* to *rootnoverify*, and to add *boot* on the line under "Chainloader +1".
It took me AAAAAAGES to figure out how to legitimately edit the menu.lst file, but I eventually did it by using *sudo gedit /boot/grub/menu.lst* from the Terminal.
I added these changes and tried it, but still no go.
It just sits there with a flashing cursor doing nothing.

Can someone please help me get back to XP?![/QUOTE]

please post your menu.lst here..

r u able to boot into ubuntu? error is only for xp boot?

---

### Post by Casgeroth on 2006-06-10
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
# kopt=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

---

### Post by Casgeroth on 2006-06-10
Booting in to Ubuntu fine (where i'm posting from now). Just not XP :(

---

### Post by glotz on 2006-06-10
(Reinstalling is overkill anyways, just "fixing" the master boot record will do. But this is your last resort.) Before it, try for example changing root (hd0,0) to root (hd0,2) or root (hd0,1). This is in your /boot/grub/menu.lst

---

### Post by Casgeroth on 2006-06-10
Ok, I've just tried changing to *root (hd0,1)* and *root (hd0,2)*.
Both times it throws this error:

[B]Error 13: Invalid or unsupported executable format.
Press any key to continue...[/B]

At which point it returns you to Grub.

Should I remove the *Boot* line from the end?

---

### Post by glotz on 2006-06-10
Hmm, maybe boot the windoze cd and select the fix option, then run **fixmbr**. That'll make windows working and ubuntu not working. Then try this [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

You need to remember how you set up your partitions (having a printout of /etc/fstab is ideal, the output of **fdisk -l /dev/hda** will also do)
 
(I'm pretty new to this all too... If you got mission critical stuff in ubuntu filesystem windoze cannot read, might be a good idea to copy it somewhere...)

---

### Post by Casgeroth on 2006-06-10
Ok, thanks. :)
Will do that next.

---

### Post by noswal on 2006-06-10
FWIW I had a similar situation, but from the other side (the dark side :) )

[http://www.ubuntuforums.org/showthread.php?t=193650](http://www.ubuntuforums.org/showthread.php?t=193650)

---

### Post by sherlock-holmes on 2006-06-10
[QUOTE=Casgeroth]Ok, I've just tried changing to *root (hd0,1)* and *root (hd0,2)*.
Both times it throws this error:

[B]Error 13: Invalid or unsupported executable format.
Press any key to continue...[/B]

At which point it returns you to Grub.

Should I remove the *Boot* line from the end?[/QUOTE]


you could varify the location from System>Administration>Disk Manager and see what NTFS says..... then try to edit the the menu.lst...

else try other suggestions in the post or reinstall grub using an ubuntu live cd...

---

