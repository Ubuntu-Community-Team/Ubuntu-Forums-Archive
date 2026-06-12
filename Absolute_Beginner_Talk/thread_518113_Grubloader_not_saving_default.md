---
title: "Grubloader not saving default"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Spaceman Spiff on 2007-08-05
Hey guys, I was wondering if anyone else is having this problem?  The grub loader won't default on the last used system, which is something I really really appreciate it being able to do.  I had debian for this and the savedefault and default saved was working, but now it always defaults to "0."  Can anyone give me some tips on this?

Also I have these questions too but I haven't researched them yet so I don't expect an answer:
  How do I remove the older kernel version (.15) I removed some base system from synaptics and I figured that would take care of its dependencies too.  I guess not though, I like not having extra stuff on my harddrives.
  Should I remove the .15 kernel version from the menu.lst after removing the .15 kernel or will grub update by itself?

menu.lst is below
> 
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
default	saved	

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
# kopt=root=UUID=f1fac3a6-a382-45d2-b4eb-aa548c0863f2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# updatedefaultentry=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f1fac3a6-a382-45d2-b4eb-aa548c0863f2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=f1fac3a6-a382-45d2-b4eb-aa548c0863f2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f1fac3a6-a382-45d2-b4eb-aa548c0863f2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f1fac3a6-a382-45d2-b4eb-aa548c0863f2 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
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


---

### Post by logos34 on 2007-08-05
run
sudo update-grub

if that doesn't clean up menu.lst, delete the -15 entries since you've uninstalled the kernel

not sure if that will correct the problem with savedefault though.

---

### Post by Spaceman Spiff on 2007-08-05
Alrighty will do, however when running a locate .6.20-15 it pulled up multiple entries of the old kernel.  Checking synaptic again I couldn't find any "green boxes" next to anything that was connected to .6.20-15 installation.

---

### Post by logos34 on 2007-08-05
> **Spaceman Spiff said:**
> Alrighty will do, however when running a locate .6.20-15 it pulled up multiple entries of the old kernel.  Checking synaptic again I couldn't find any "green boxes" next to anything that was connected to .6.20-15 installation.

maybe you did 'mark for removal' as opposed to 'complete removal'

---

### Post by Spaceman Spiff on 2007-08-05
Alright, I'll check that out logos34.  Would you happen to know why grub isn't defaulting to the last operating system.  I can't understand why savedefault and defaulted saved isn't working.  Any tips?

---

### Post by logos34 on 2007-08-05
I have mine set up just like yours -- 'default saved'.  I can't spot any errors in it except I did notice one difference--mine reads:

> v## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=**false**

just not sure why it doesn't work for you anymore.  Your winxp entry has 'savedefault' like the others

---

### Post by Spaceman Spiff on 2007-08-05
Could you post your menu.lst?  And does yours default correctly?  Also what version of grub loader are you using?  Perhaps its a version problem.

---

### Post by Spaceman Spiff on 2007-08-05
By the way logos you were right about that "complete" removal stuff, thanks man.

---

### Post by Spaceman Spiff on 2007-08-05
OKAY, so I have been messing around and I have the problem singled out to a distinct event.  I am pretty sure that the reason its not defaulting to the last operating system used is because the default file isn't being read or being read incorrectly.

I checked the default file after logging into the two boot options that do the savedefault command and saw that the default file was changing correctly.  Then I set the default file manually (grub-set-default 4) and i checked it in the grub loader command console at start up (cat /boot/grub/default) and it still defaulted to 0 (the first operating system on the list, not the 4th even though the default file had a 4 in it)  Finally, I decided to hardcode a default, and changed my menu.lst to default 4, and it defaulted to windows xp as i wanted it to.  

So, in conclusion, I am pretty sure that the grub loader is simply not reading the default file and in such case defaulting to 0.

Anyone got any thoughts? Any solutions?

---

### Post by logos34 on 2007-08-06
I just read over the relevant sections of the GNU Grub 0.97 manual and can't find any possible solutions to your problem.  I just tested mine and everything appears in order--both by invoking 'grub-set-default' command and when I manually edit the 'default #' in menu.lst.  The /boot/grub/default file is changing correctly and the new kernel entry boots up as it should.  I have mine set as 'default  saved' (currently '0', my -16 Feisty kernel) and then I did 

**sudo grub-set-default 2**

and the third 'title' line (remember, grub starts counting from **0**) boots up just as it's supposed to (i.e. my -15 kernel).

'**ls -l /boot/grub/default**' should show the following permissions:

> -rw-r--r-- 1 root root 197 2007-07-17 22:43 /boot/grub/default

What I don't understand is how you're getting the windows entry to boot with 'default 4': grub starts counting (from 0) all 'title' lines without a '#' mark (*including the **'Other operating systems'** line), and since your winxp entry is the 7th title line down (**0**,1,2,3,4,5,**6**), the correct command to boot winxp by default should be

**sudo grub-set-default 6**

or edit menu.lst thus:

**default  6**

Maybe there's a tiny formatting error in your /boot/grub/default file.  Here's mine:

> 2
#
#
#
#
#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using `grub-set-default\' is
# strongly recommended.


But I wouldn't copy and paste that.  In fact, don't directly edit it (like it says).  If only you could just replace it with a fresh copy, but I don't see one in /usr/lib/grub/i386-pc.

Wish I knew the answer to this.

Here's my menu.lst you requested:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

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
# kopt=root=UUID=47265b51-a7fc-437e-ae4c-fa649fa3194b ro

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
# defoptions=splash

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
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=47265b51-a7fc-437e-ae4c-fa649fa3194b ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=47265b51-a7fc-437e-ae4c-fa649fa3194b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=47265b51-a7fc-437e-ae4c-fa649fa3194b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=47265b51-a7fc-437e-ae4c-fa649fa3194b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

#title		Ubuntu, kernel 2.6.17-11-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro splash
#initrd		/boot/initrd.img-2.6.17-11-generic
#boot

#title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.17-11-generic
#boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.17-10-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Boot from CD (SBM)
root		(hd0,2)
kernel		/boot/memdisk
initrd		/boot/sbm.img

title Ubuntu installer
root (hd0,7)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz

title Ubuntu installer (2)
root (hd0,8)
kernel   /linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   /initrd.gz

title DSL installer
root (hd0,7)
kernel /KNOPPIX/memdisk boot=KNOPPIX root=/dev/ram ramdisk_size=1048576 rw
initrd /KNOPPIX/boot.img

title		Ubuntu 7.04 x86_64, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8e7068de-b412-47c2-b04c-e603c993d408 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu 7.04 x86_64, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8e7068de-b412-47c2-b04c-e603c993d408 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.04 x86_64, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e7068de-b412-47c2-b04c-e603c993d408 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu 7.04 x86_64, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e7068de-b412-47c2-b04c-e603c993d408 ro single
initrd		/boot/initrd.img-2.6.20-15-generic


---

### Post by Spaceman Spiff on 2007-08-07
Oh yeah ludos you're right, but I deleted the boot lines for the .15 kernel because the image files were deleted by synaptic so they were pointless.  Anyways, I figured out the solution, it's so dumb

SOLUTION:
  Everything was reading correctly, my first thoughts were completely wrong.  The fault, I believe (because it worked after this) lay in the default line, mine looked something like this
"default saved    " notice there were some extra white space after the saved, I believe that threw it off.  I noticed this when I hardcoded a default entry into the default, and decided I would go back to saved, and noticed that manually changing the default file all of a sudden worked.  So no extra spaces after saved :-x

---

### Post by logos34 on 2007-08-07
> "default saved " notice there were some extra white space after the saved, I believe that threw it off. I noticed this when I hardcoded a default entry into the default, and decided I would go back to saved, and noticed that manually changing the default file all of a sudden worked. So no extra spaces after saved

glad you managed to fix it...hmm, the space after saved, I'll have to remember that.  I would never have thought of that, although I'm fully aware what a world of difference an errant space can make WITHIN a line in menu.lst (like on a 'kernel' or 'map' line)

---

