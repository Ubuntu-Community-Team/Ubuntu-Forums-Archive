---
title: "Hmm, Vista doesn't Want to boot up..."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Nudgeworth on 2007-09-19
Hello, 
 I've been Dual booting Ubuntu and Vista for several months now with no problem.

 Now suddenly Vista won't boot, I select it in GRUB and then it hangs.

 I can still see The Vista Partition in the file browser.

  Any ideas anyone?

---

### Post by Nudgeworth on 2007-09-19
bump

---

### Post by kellemes on 2007-09-19
Can you post /boot/grub/menu.lst please?

---

### Post by Nudgeworth on 2007-09-19
Will do, but how do I find it?

---

### Post by AliL on 2007-09-19
> **Nudgeworth said:**
> Will do, but how do I find it?

Ok, go to places on your menu bar, and click on Computer. Then select filesystem. You should now have a window with about 20 folders in it. Select the folder called boot. In that, select the folder called grub. Then open the file called menu.lst. Once open, press Ctrl+A to select everything and then Ctrl+C to copy it. Then go to your browser and open a reply to this topic and paste in the contents in a code box which can be found on the row of tools at the top of the reply box that looks like this: # 
You paste using Ctrl+V.

Hope this helps.

AliL

---

### Post by Nudgeworth on 2007-09-19
Whoops I feel asleep.

 Thanks Alil.

 And here is my menu.lst file

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
# kopt=root=UUID=62c15d86-18d8-4233-8ef7-49c15c265167 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=62c15d86-18d8-4233-8ef7-49c15c265167 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=62c15d86-18d8-4233-8ef7-49c15c265167 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=62c15d86-18d8-4233-8ef7-49c15c265167 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=62c15d86-18d8-4233-8ef7-49c15c265167 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by CaptainInsaneO on 2007-09-19
Have you tried booting both of those entries? (You have one Vista entry at hd0,0 and one at hd0,1)

---

### Post by Nudgeworth on 2007-09-19
yeah, one is the normal boot up for vista, the other is the recovary manager. Which doesn't seem to be much help.
 Unless I want to reinstall Window's, which i think will destroy the Ubuntu Partition

---

### Post by anemptygun on 2007-09-19
Just out of curiosity what version of vista is it?

---

### Post by Nudgeworth on 2007-09-19
> **anemptygun said:**
> Just out of curiosity what version of vista is it?

 Basic.

  I bought myself a computer I could afford afford, and it came with Vista. I had no choice in the matter.
 Slow loadind times, sluggish performance, I would have been better off with XP, But then I wouldn't have discovered Ubuntu lol

---

### Post by CaptainInsaneO on 2007-09-19
Have you gone into Partition manager (in Ubuntu) and made sure the Vista partition is flagged as bootable? (Should have a star/asterisk next to it)

---

### Post by anemptygun on 2007-09-19
oh ok, I was just wondering if it was a release canidate or something...

---

