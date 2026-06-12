---
title: "[SOLVED] prevent &amp;quot;updates&amp;quot; to grub's menu.lst"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by redyoshi49q on 2008-02-10
I got Ubuntu on my system so that I could boot my system into a graphical interface if Windows decided to die (which has happened more times than I care to count).  Ubuntu's working beautifully as an alternate operating system.

Having said that, I have a tiny grub problem.  I did a heap of updates, and one of the updates (presumably a grub update?) "updated" my menu.lst file.  This nuked XP from my boot menu.  Fortunately, I was eventually able to bring it back, but unfortunately, I decided that trying the proprietary NVidia driver would be a good thing to do in the meantime. (The driver gave me a blank screen, but got this fixed, too.)  My stupidity left me without a functional GUI environment for a decent period of time, which was exactly what I was trying to avoid in the first place.

How do I set up grub so that it will both keep the XP boot info and modify menu.lst if and when Ubuntu's kernel changes for some reason?  If setting up grub like this is possible, does having a customized title for the boot option confuse this feature?  Am I doomed to keeping a backup copy of the menu.lst file in case of emergency?  It seems like one of the options in menu.lst might be the solution, but I'd rather not tinker with random things in grub...

Thanks in advance. :)

---

### Post by asmoore82 on 2008-02-10
this may be helpful...
[http://ubuntuforums.org/showthread.php?p=4276718#post4276718](http://ubuntuforums.org/showthread.php?p=4276718#post4276718)

---

### Post by spiderbatdad on 2008-02-10
if you use the method of editing the default number, than an upgrade should only overwrite 0, at worst you would have to change the number again. If you use the method of moving windows into the first position in the list, then it would be advisable to copy and paste...leaving the other windows text block listed...you could comment out the lines to prevent it from showing up twice in grub at boot up.

---

### Post by erfahren on 2008-02-10
What do you mean by "custom boot title" 

I've never had a problem with any update messing up the menu.lst or removing entries - and I have mine fairly modified.

post your menu.lst here and let us take a look at it.

---

### Post by redyoshi49q on 2008-02-10
Thanks for your help, you guys!  The dual booting guide that I found online forgot to mention that XP is best put *outside* of the automagic kernels section.  It's hard to tell if my problems fixed now, but it seems like my current setup would be more likely to survive a grub update.

If it's still important, below is my menu.lst, recent modifications included.

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

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

# This is a divider
title		Microsoft:
root

# This is a divider
title		-Windows:
root

title		--Windows XP SP 2
root		(hd0,1)
makeactive
chainloader	+1
savedefault

# This is a divider
title		Linux:
root

# This is a divider
title		-Ubuntu:
root

## end static boot stanzas

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
# kopt=root=UUID=ceed3a2f-c247-44fd-a0cd-07272d63ceab ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# lockold=true

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

title		--Ubuntu 7.10
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ceed3a2f-c247-44fd-a0cd-07272d63ceab ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		--Ubunto 7.10 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ceed3a2f-c247-44fd-a0cd-07272d63ceab ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		--Ubuntu 7.10 memtest
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by ugm6hr on 2008-02-10
> **redyoshi49q said:**
> The dual booting guide that I found online forgot to mention that XP is best put *outside* of the automagic kernels section. 

That is the important bit!  The updates will automatically change all the entries within the automagic section - hence the "lost" XP!

Looks like you should be OK from now on.

Just waiting for the "savedefault" to be switched to Ubuntu now ;)

---

### Post by erfahren on 2008-02-10
> **redyoshi49q said:**
> ... The dual booting guide that I found online forgot to mention that XP is best put *outside* of the automagic kernels section. 

oh, most *definitely*! That would have posed a problem. (actually it says something to that effect in the file - lol )

I like how you have that set up though - pretty good idea - so the menu looks like:

Microsoft
-Windows
--Windows XP SP 2
Linux
-Ubuntu
--Ubuntu 7.10

Anyway - I like the  guide on GRUB at Hermanzone's site - it's real thorough: [Hermanzone's GRUB page](http://users.bigpond.net.au/hermanzone/p15.htm)

glad you got it figured out

---

