---
title: "Setting up the boot screen"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-17
I have recently installed Ubuntu in a partition, next to my xp OS.

I want to set xp back as the default os, and to use Ubuntu press a special key, like escape or the like, during the startup.

Please help, and thanks in advance

---

### Post by NetworkGuy on 2006-11-17
I recommend you continue using Grub for your boot manager and just make a change to get it to boot Windows XP instead of Ubuntu.  

In /boot/grub there is a file called menu.lst.   This file needs to be edited so that it will boot Windows XP by default.

MAKE A BACKUP COPY OF THE FILE BEFORE YOU DO ANYTHING. :)

I don't have my Ubuntu booted right now (at work) but in the file you will see the entry that allows you to choose what grub will default boot to.   (Read the comments for each command to help find the right one)

You need to change the number from 0 to the number assigned to Windows XP.  The easiest way I found to do this was to boot your Pc and press esc when asked.  Starting at 0 count up (0,1,2,3)until you highlight the XP entry (don't count the "other operating systems line).

Save your menu.lst and reboot.  

I can't stress enough that making changes to this file incorrectly will blow grub up.

If you want, you can post your menu.lst and we can help verify the correct entries for you.

---

### Post by japc126 on 2006-11-17
Another thing, grub (whatever) lists my xp as vista/longhorn, but it still boots as xp. There is no problem in that, right?

---

### Post by japc126 on 2006-11-17
I changed the 0 to a 3 and entered the command hiddenmenu. I copy here all the text until the point where I modified it

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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
hiddenmenu

---

### Post by japc126 on 2006-11-17
The changes are not working because "I'm not the owner" what can I do?

---

### Post by nickpaton on 2006-11-17
Can I suggest that you post all of your grub menu, coz your boot number may not be 3 to get XP as the default - it depends on what else you have loaded.

---

### Post by japc126 on 2006-11-17
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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
hiddenmenu

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
# kopt=root=UUID=730cf83c-aad6-495e-930a-5dc36d17923e ro
# kopt_2_6=root=/dev/sda5 ro

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

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by nickpaton on 2006-11-17
> **japc126 said:**
> The changes are not working because "I'm not the owner" what can I do?

To backup (It is V important):

```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
```

In the meantime do a copy / paste and maybe print it out, so if things go wrong, at least you can retype it in!!

To modify:

```
 gksudo gedit /boot/grub/menu.lst
```

Gives you permissions to edit.  Ignore error messages, and remember to save afterwards.

Oh and to boot into XP is 3!

---

### Post by japc126 on 2006-11-17
This is going to sound totally stupid but well....

where do I type "gksudo gedit /boot/grub/menu.lst"

---

### Post by japc126 on 2006-11-17
what about the command hiddenmenu? is it correct?

by the way, I found the terminal.

---

### Post by nickpaton on 2006-11-17
> **japc126 said:**
> This is going to sound totally stupid but well....

where do I type "gksudo gedit /boot/grub/menu.lst"

Not stupid at all so don't worry LOL

You do all these types of commands in a Terminal, which you will find via Applications > Accessories > Terminal.

A box with a black background will open with the following (in my case):

> nick@nick-laptop:~$

You type the commands after this prompt.  
I suggest doing a copy from the posts, and pasting into the Terminal.

After you have entered each command, press enter to make it run.

Some will appear to do nothing, other than return to the prompt.

Others will ask for a password, and you enter the password you log in with.

Occasionally an error message will appear and a couple of seconds later a new window will open (as will happen with Grub.list).  Ignore the error message which is a bug apparently.

Lots of really good information can be found at

[http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

and Psychocats:

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

HTH - get back with any problems etc.

---

### Post by Tomosaur on 2006-11-17
You may want to check the link in my sig, it'll let you set up Grub to do what you want to do :)

---

### Post by nickpaton on 2006-11-17
> **Tomosaur said:**
> You may want to check the link in my sig, it'll let you set up Grub to do what you want to do :)
Forgot about that - I even use it and recommend it too!!

---

