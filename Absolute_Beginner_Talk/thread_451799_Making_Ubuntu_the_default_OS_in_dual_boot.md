---
title: "Making Ubuntu the default OS in dual boot"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-22
I have a dual boot system of XP/Ubuntu and if I do nothing at boot up Windows boots up !!

Is there away to make Ubuntu boot up as default if I do nothing at the grub selection screen ??

If it is possible please do it step-by-step as simple as possible PLEASE !!

---

### Post by Ek0nomik on 2007-05-22
I am not 100% sure, but I **think** this will work...

I presume Windows is the first choice in your Grub Menu?

```
sudo gedit /boot/grub/menu.lst
```

Then simply change the order of the Titles at the very bottom of the page.  (Copy and pasting the multi-line entries should take care of it)

---

### Post by taurus on 2007-05-22
Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the default value from whatever it is to 0, first entry.

```
default     0
```
Save it and reboot.

---

### Post by Cloudedbrains on 2007-05-22
Ok I am totally confuddled what to alter :(

Here is what that command opens up ;)

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
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title		Ubuntu, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
```

So what exactly do I do to THAT lot to make Ubuntu boot as default and not Windows :o
**At present WINDOWS is default :(**

I am recently new to this so SIMPLE terms please :D

---

### Post by Cloudedbrains on 2007-05-22
Help someone - begging nicely for help [-o<[-o<[-o<[-o<[-o<[-o<

---

### Post by Ek0nomik on 2007-05-22
**Backup** your menu.lst file,

Try changing the 0 to a 1.  Reboot.  Let me know if it worked.

---

### Post by steve.horsley on 2007-05-22
I don't see an entry for windows at all in that file. Are you sure you posted the right /boot/grub/menu.lst file? Could there be another such file on another partition?

I don't recognise the /wubi stuff in the Ubuntu stanzas either. This is not the standard Ubuntu install, I think. Is there any other information we should know?

---

### Post by taurus on 2007-05-22
Or did you even install GRUB to MBR?

---

### Post by Cloudedbrains on 2007-05-22
I installed Ubuntu via Wubi - and XP was on pc to start with :(

```

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
```

is taken from the above file and DOES mention windows ;)

WHICH 0 am I meant to be changing could you quote the code line I need to alter :p

If that shortens the boot time thats not what I need - I get offered **[COLOR="Red"]XP top of list[/COLOR]**
and **[COLOR="Blue"]Ubuntu 2nd on list[/COLOR]** when PC boots and without manually choosing Ubuntu it boots to windows by default :(

I want it to boot to Ubuntu to default :D

---

### Post by init1 on 2007-05-22
Anything in "#" is a comment. It won't be used unless the "#" is removed. The code that mentions Windows should not do anything. I think they wanted you to edit the "Default 0" at the top to "Default 1", but I don't understand how windows can load if it is not in you menu.lst. Try reinstalling grub if all else fails.
grub-install /dev/???
Where ??? is your HD drive. hda is most likely case.
grub-install /dev/hda 
should work
Someone please confirm this. It's been awhile since I have done this sort of thing
Then try giving us the menu.lst dump

---

### Post by louieb on 2007-05-22
Y say you installed Ubuntu via **wubi what the heck is that** never seen a menu.lst like yours. interested now guess i go google it.

---

### Post by Clay_Banger on 2007-05-22
i believe that you will need to edit the boot.ini in c:\

switching the items around should do the trick.

ie:
```
long string of junk that loads windows
another long string that loads grub
```
change to:
```
another long string that loads grub
long string of junk that loads windows
```
post you boot.ini if you think you may have problems

---

### Post by louieb on 2007-05-22
> **louieb said:**
> Y say you installed Ubuntu via **wubi what the heck is that** never seen a menu.lst like yours. interested now guess i go google it.
Did a Google and look what I found [Wubi - The Easiest Way to Linux]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")
Installs its self inside of windows.
[and from the ubuntu wiki]("https://wiki.ubuntu.com/WubiGuide")

**How do I make Ubuntu the default boot option?**

  Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well.

[CENTER][SIZE=3][COLOR=Cyan]Google is your friend[/COLOR][/SIZE]:guitar:[/CENTER]

---

### Post by Cloudedbrains on 2007-05-23
> **louieb said:**
> Did a Google and look what I found 
**How do I make Ubuntu the default boot option?**

 Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well.


Oh you NICE NICE [SIZE="5"]NICE[/SIZE] person ):P
Thankyou that solved it :razz::razz::razz::razz::razz:

---

### Post by Cloudedbrains on 2007-05-28
Ok after trying single boot without windows am in process of getting back to dual boot as there were chunks of software that wouldnt run on Ubuntu that I needed so am back on windows but gotta set up the dual boot now :)

This is Wubi:
[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

