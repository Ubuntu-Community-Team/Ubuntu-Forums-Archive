---
title: "Ubuntu 7.10 on Macbook Pro Santa Rosa - Few issues"
date: 2008-03-22
forum: Apple Intel Users
---

### Post by Dark_Lotus on 2008-03-22
I have Ubuntu 7.10 installed on my Macbook Pro as the primary OS. No windows, no OS X, just Ubuntu. On startup I see the same screen that has the apple on it but with no apple, then a black screen, a few flashes, then the ubuntu login screen. Is this normal? Is there no boot image for ubuntu?

---

### Post by tvtech on 2008-03-22
not sure if this is normal.  are you using the grub-efi boot loader?  or something else?

usual experience is to see the script loading screens and then a ubuntu log in time bar then the log in screen.  but that is with standard bios not efi

---

### Post by Dark_Lotus on 2008-03-22
Umm, I see something about grub on startup. It says GRUB loading stage 1.5 then something, then "Starting up..." then its a black screen for a while then the Ubuntu login screen shows up.

---

### Post by cyberdork33 on 2008-03-23
It sounds like the bootspash is using the wrong resolution for some reason. This was an issue for a lot of people in Gutsy. I do not have the fix handy, but I know that it is all over the forums.

---

### Post by Dark_Lotus on 2008-03-23
Okay, thanks I'll try to look for it. I edited the config file to a supported resolution but still nothing. Why does the apple screen show up with no apple logo though? does this have something to do with only running ubuntu without OS X?

---

### Post by Dark_Lotus on 2008-03-23
Now that I look at it closer, the screen completely shuts off in between displaying the grub menu and the login screen. Any ideas?

---

### Post by cyberdork33 on 2008-03-23
> **Dark_Lotus said:**
> Now that I look at it closer, the screen completely shuts off in between displaying the grub menu and the login screen. Any ideas?The apple only shows when OSX loads.

It still sounds like the same problem with the bootsplash resolution. You might have to try lower resolutions than you have already tried. Also, if you edit the menu.lst entry for your kernel and remove the quiet options, then you should be able to see the system messages during bootup instead.

---

### Post by Dark_Lotus on 2008-03-24
I've tried everything it feels like. I tried changing the resolution to the lowest possible one and still nothing. I understand that it wouldn't display a clear image with the wrong resolution but if the display is completely shutting off isn't this another problem?

---

### Post by rakan21 on 2008-03-24
Well im guessing this is probably normal. It matters wether you should fix it or not on how fast it loads if it takes more than 30 seconds then yeah fix it, but if it gets you into the login screen and you its under 30 secs well then you have an OS without a Bootscreen which I find that to be good. 

Anyway I need help on Installing Ubuntu myself. I burn't it to a CD and all that ****. When i reboot should i click ALT and wait for the two HD to load (Mac Windows, Usually when I insert a windows CD its displayed in Bootcamp). Because after I insert it it automatically goes into Mac OS X. So what should I do.

---

### Post by Dark_Lotus on 2008-03-24
You have to hold down the 'c' key and make sure you have properly burnt the ISO to the CD with a program like disk utility.

It just bothers me not having a boot screen. When I remove the quiet options the screen doesn't turn off in between the GRUB menu and the login screen. So it has to be something with when the splash is displayed that the screen turns off. Any ideas?

---

### Post by cyberdork33 on 2008-03-24
> **Dark_Lotus said:**
> It just bothers me not having a boot screen. When I remove the quiet options the screen doesn't turn off in between the GRUB menu and the login screen. So it has to be something with when the splash is displayed that the screen turns off. Any ideas?
Yep that is what I was expecting. Check your menu.lst. Please post it. I am guessing to tried to specify a resolution on the install disc or something, and now it tried to use that as the default, and messes things up. My mac does the same thing if i try to set the resolution in the framebuffer.

---

### Post by sunbird on 2008-03-27
I have a similar problem on my machine. I am in the process of doing a reinstall to crypt the ubuntu partition. I'm concerned that the resolution problems during startup may mean that I never get the screen to input my passphrase. 

I'm also concerned because it does take more than 30 seconds to load, so I'd like to see the splash screen.

Can someone post a specific fix that has worked?

**EDIT:** As I suspected, I can't see the screen when it asks me for my PW. Any fixes?

**SOLUTION:** 

I changed "splash" to "nosplash" in menu.lst which fixed the problem (mostly). The wrapping of the text on startup is strange, but at least I can see it.

Here's my menu.lst (located in /boot/grub/menu.lst):

(note that you'll need to run sudo grub-install after modifying)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=/dev/mapper/sda4_crypt ro

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
# defoptions=quiet nosplash

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/sda4_crypt ro quiet nosplash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/sda4_crypt ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by rakan21 on 2008-05-19
I finally got Ubuntu 8.04 and installed it on my Macbook. You don't actually have to click C just alt after you insert the CD. What I did wrong was burning the .iso. i burnt the actually .iso instead of all the files.

---

