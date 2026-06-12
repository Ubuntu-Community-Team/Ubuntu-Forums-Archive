---
title: "I am trying to change the boot order in Grub, not sure how..."
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by AirDemon on 2006-07-26
I am familiar to a small existent with the Terminal

 /boot/grub/menu.lst

is where I thought it would be but I can't get into it because I am not logged in? 

I am sure this is a very simple thing to explain I guess I am just logging in wrong....

In my defense I only installed Ubuntu today and have never used Linux before in my life so I am doing okay at least =p

---

### Post by scxtt on 2006-07-26
you'll have to be a little more explicit in the problem - are you getting an error message?

if you're not logged in, you won't be able to edit anything - there's not really a wrong way to login, if you're in ...

---

### Post by aysiu on 2006-07-26
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by stlutz on 2006-07-26
Hope you're enjoying Ubuntu thus far.

This is a permission issue, and easy to address.

First, to explain the issue:  From your command line, you can type:  ls -laF /boot/grub/menu.lst

This will provide the following output (or something very similiar):

-rw-r--r-- 1 root root 5520 2006-06-15 20:55 /boot/grub/menu.lst

This indicates that the owner of the file can read and write it ("rw"), that members of the owners group can read it (the first "r"), and that anyone can also read it (the second "r".).  The first "root" indicates that the root user is the owner.  The second "root" indicates that root is a member of the root group.

In short, this is telling us that only the root user can modify ("write") the file.  To do that, you will use the "sudo" command.

To do that, 1) change to your /boot/grub directory by typing "cd /boot/grub"
2) Back the file up before changing it:  "sudo cp menu.lst menu.lst.bak".  Enter your password when prompted
3) Type "gksudo gedit menu.lst".  (I used "gksudo" since I'm opening a grpahical program).

Now you can make your changes.  Be careful when making changes to the file since this does affect booting your system.

For more on all of this, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AirDemon on 2006-07-26
thx, I will try that

---

### Post by AirDemon on 2006-07-26
okay I got into it but I am not sure how to edit it...

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
default		3

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
# kopt=root=/dev/sda2 ro

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
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
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by AirDemon on 2006-07-26
bah, and it seems to be read only...

---

### Post by scxtt on 2006-07-26
what are you trying to accomplish?

use **sudo vi /boot/grub/menu.lst** ... or **gksudo gedit /boot/grub/menu.lst** ...

---

### Post by aysiu on 2006-07-26
If you want Windows to be the default, change this ```
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
**default 3**
``` to this ```
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
**default 6**
``` Since Windows is the 7th entry, and numbering starts at 0.

---

### Post by AirDemon on 2006-07-26
lol, sorry, I want Windows to be the default since I still use that for most of my aplications

---

### Post by aysiu on 2006-07-26
> **AirDemon said:**
> bah, and it seems to be read only...
Did you read the links people posted? Of course it's read-only. It's a system file.

In order to edit it, you have to temporarily assume administrative privileges. ```
sudo nano -B /boot/grub/menu.lst
``` or ```
gksudo gedit /boot/grub/menu.lst
```

Please take the time to read the links people took the time to type out for you. These links will help you understand what you're doing!

---

### Post by AirDemon on 2006-07-26
okay done, I will se if it works, thx for helping out a noob =p

---

### Post by AirDemon on 2006-07-26
> **aysiu said:**
> Please take the time to read the links people took the time to type out for you. These links will help you understand what you're doing!

I read it, I just typed the wrong thing... I figured it out like 2 seconds after I posted, sorry  about that

---

### Post by aysiu on 2006-07-27
> **AirDemon said:**
> okay done, I will se if it works, thx for helping out a noob =p
Did you make a backup copy of that file? If not, you should definitely do that: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by AirDemon on 2006-07-27
Yes, I backed up, and it worked, thx for all your help

---

