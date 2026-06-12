---
title: "exXP"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by exXP on 2007-05-10
When it gets going I love Ubuntu.  However it takes as long as Windows XP to boot and while it's booting the screen is absolutely blank.  I don't want anything as exciting as Knoppix gives while loading, but some indication on the screen that there is intelligent life inside the box would be welcome.  I s there something out there thst I've missed?
exXP  (and not going back!)

---

### Post by drowner on 2007-05-10
> **exXP said:**
> When it gets going I love Ubuntu.  However it takes as long as Windows XP to boot and while it's booting the screen is absolutely blank.  I don't want anything as exciting as Knoppix gives while loading, but some indication on the screen that there is intelligent life inside the box would be welcome.  I s there something out there thst I've missed?
exXP  (and not going back!)

Mine says 'Ubuntu'

---

### Post by Najand on 2007-05-10
Can't you see any splashscreen like the following?

---

### Post by exXP on 2007-05-10
No!  Absolutely nothing.  I downloaded 7.04 from one of the sites and burned a CD.  This is probably only a small complaint but since I don't leave my computer on all the time I reboot 2 or 3 times a day.
exXP

---

### Post by lamalex on 2007-05-10
beck your /boot/grub/menu.lst file it should look something like this

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-686
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

notice this:
```
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

```
part. Yours will look a bit different depending what version of Ubuntu you're using. Make sure Splash is enabled, it's possible you have quiet but no splash, alternately you could just remove quiet and not add splash, or add splash and remove quiet (my preferred set up on my pc, this is my work computer).

---

### Post by Sef on 2007-05-10
Once it boots up is there any problems?

---

### Post by Najand on 2007-05-10
Open a terminal (Applications -> Accessories ->  terminal) and type:
```

sudo apt-get install usplash usplash-theme-ubuntu

```
push enter then when asked enter your password.

---

### Post by srt4play on 2007-05-10
Sounds like the wrong video mode is being used during boot.

When you see the GRUB splash ("press esc to enter the menu"), press escape.  Highlight the top entry and press "e".   Highlight the line starting with "kernel" and press "e".  Add "vga=771", without the quotes, to the end of the line and press enter.  Make sure the line starting with "kernel" is still highlighted and press "b".  

If it works, let us know and we'll make it permanent.  If it doesn't work, retry with "vga=791".

---

### Post by exXP on 2007-05-10
Thank you all for your suggestions.  Unfortunately I have not been able to make them work.  On the suggestion of altering the grub/menu file I was denied permission to make the change.  What I could probably do is to load Knoppix and use that to make the change.
Otherwise I am pleased to state that Ubuntu is working well except for my scanner - and I gather is not just my problem!
I may decide that it's not a big thing and forget about it
exXP

---

### Post by srt4play on 2007-05-10
Did you see any change at all when adding the "vga=xxx" line?

---

### Post by exXP on 2007-05-10
Unfortunately I posted reply before I received the post from srt4play.  THIS WORKS!!! and furthermore reduces the boot time dramatically.  Thank you.  Now I would love to know how to make it permanent.
exXP

---

### Post by srt4play on 2007-05-10
Alt-F2 to bring up mini command prompt

gksudo gedit /boot/grub/menu.lst

find the first entry for ubuntu towards the bottom and add vga=771 to the end of the kernel line.

---

### Post by Najand on 2007-05-10
You need to edit your "/boot/grub/menu.lst" file.
At the bottom of the file you will find something similiar to the one you edited during boot. Edit it and save it.

---

### Post by exXP on 2007-05-10
To  srt4play  -  thank you again.  This is a double success, it answers both my complaints at the same time making Ubuntu even more of a joy to work with.
exXP (and even less reason to go back)

---

### Post by srt4play on 2007-05-10
Good job exXP, way to go!

---

