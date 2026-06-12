---
title: "Option to start Windows xp have disappeared from grub Bootloader"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by thort on 2006-02-10
Hi !

Peculiar! The option to start Windows XP have suddenly disappeared from my grub bootloader. I don't know how it happened.

Here is the content of my **menu.list**:

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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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

title		Ubuntu, kernel 2.6.12-8-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-8-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-8-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

How do I write an option making it possible to choose to start Windows XP in the startmenu of the bootloader?

---

### Post by ymmotrojam on 2006-02-10
Your Grub menu list is backed up after every change (only one backup is kept that I know of, which would be before the last change)... go here and see if it contains the boot informtion you need... and you can copy/paste it into the current menu again...

In the terminal... (note the tilda on the end)
gedit /boot/grub/menu.lst~

---

### Post by lha on 2006-02-10
[QUOTE=thort]Hi !

Peculiar! The option to start Windows XP have suddenly disappeared from my grub bootloader. I don't know how it happened.

Here is the content of my **menu.list**:

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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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

title		Ubuntu, kernel 2.6.12-8-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-8-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-8-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-8-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

How do I write an option making it possible to choose to start Windows XP in the startmenu of the bootloader?[/QUOTE]

I bet your Windows entry was between lines
### BEGIN AUTOMAGIC KERNELS LIST
and
### END DEBIAN AUTOMAGIC KERNELS LIST
All lines between those two are removed and recreated (usually two entries for each kernel you have) when you upgrade kernel. As you don't have Windows kernel :) in Ubuntu, Windows wasn't recreated.

Paste these lines in the very end of menu.lst, under the line '### END DEBIAN AUTOMAGIC KERNELS LIST'
```
title Windows
root (hd0,0)
savedefault
makeactive
chainloader +1
```

You might need to change (hd0,0) to something else if you have installed Windows  and Ubuntu using non-standard way.

---

### Post by thort on 2006-02-10
Thanks ymmotrojam and Iha !

I will try your suggestions tomorrow. I post the result.

---

### Post by thort on 2006-02-11
My problem is solved!

I picked up my old Windows xp setting from the backup file,  **/boot/grub/menu.lst~**. Then I pasted the setting into my current **menu.lst**. And voila, I got the Windows xp start option back in my grub bootloader.

Very good! Thanks once more for your help!  :)

---

### Post by Lord Illidan on 2006-02-11
Re: GRUB and Windows, I often upgraded my kernel, and an extra entry would appear at boottime, but it never deleted Windows from the list.

---

