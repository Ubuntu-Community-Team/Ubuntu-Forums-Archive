---
title: "how do i get rid of grub menu"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-19
hello guys,

i wanted to get rid of grub menu.. it was siimpler and faster before when i directly booted to splash screen but dont know why. now it lists all the kernel and i have to chose one then press enter and all that crap.. how do i change to how it was.. ..

---

### Post by HunkieChan on 2007-03-19
anyone please ?

---

### Post by HunkieChan on 2007-03-19
anyone ?

---

### Post by floke on 2007-03-19
Do this.
First make a backup - sudo cp /boot/grub/menu.lst cp/boot/grub/menu.lst_backup
Then - sudo nano /boot/grub/menu.lst

You can then either change the timeout value to 0 or unhash the hiddenmenu option

---

### Post by HunkieChan on 2007-03-19
> **Steve.K said:**
> Do this.
First make a backup - sudo cp /boot/grub/menu.lst cp/boot/grub/menu.lst_backup
Then - sudo nano /boot/grub/menu.lst

You can then either change the timeout value to 0 or unhash the hiddenmenu option

i did that.. doesnt work

---

### Post by Henry Rayker on 2007-03-19
Just a word of advice...don't bump your thread until it's been around for a reasonable amount of time...ten minutes is not enough time. This kind of activity tends to piss people off and make them just not really feel like helping you.

Steve offered two possibilities...did you try both? What happens when you do each? The hiddenmenu option should do what you want, I believe.

---

### Post by floke on 2007-03-19
Ditto. Only noticed that after I'd answered the question, else I might not have bothered.

---

### Post by HunkieChan on 2007-03-19
> **Henry Rayker said:**
> Just a word of advice...don't bump your thread until it's been around for a reasonable amount of time...ten minutes is not enough time. This kind of activity tends to piss people off and make them just not really feel like helping you.

Steve offered two possibilities...did you try both? What happens when you do each? The hiddenmenu option should do what you want, I believe.

im sorry, i dont have patience

yes i did what i asked me to .. but it doesnt work.. any other options ?

---

### Post by mahiyar on 2007-03-19
Please post the relevant portions of menu.lst (where you made the changes). And learners (includes me and I guess everybody) should have patience.

---

### Post by HunkieChan on 2007-03-19
> **mahiyar said:**
> Please post the relevant portions of menu.lst (where you made the changes). And learners (includes me and I guess everybody) should have patience.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		X_sequence

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		X_seconds

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
# kopt=root=UUID=09237b17-7526-4219-983e-a738c1061f7c ro
# kopt_2_6=root=/dev/sda2 ro

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

#title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

#title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

#title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by floke on 2007-03-19
Looking at this it's clear you didn't have the patience to follow the instructions properly.

---

### Post by mahiyar on 2007-03-19
Whats that  timeout		X_seconds; it should read timeout  10 (for 10 seconds delay) or timeout 0 (for zero seconds delay). I would personally advice you to keep timeout as 2, certainly you can bear 2 seconds delay, this gives a chance to "ESC" if in case of problem you want to do anything from grub menu.

---

### Post by mahiyar on 2007-03-19
The same problem is in the  "default		X_sequence" line just above time out. By default it should be "default 0". Hope you have backed up this (menu.lst) file.

---

### Post by HunkieChan on 2007-03-19
i did all that from ubuntuguide.org... i thought that was a reliable source

---

### Post by mahiyar on 2007-03-19
ubuntuguide.org is reliable. When they say X_something it means you are supposed to replace that with an appropriate numeral. My my are we hasty or what, but at least we are learning :)

---

### Post by HunkieChan on 2007-03-19
> **mahiyar said:**
> ubuntuguide.org is reliable. When they say X_something it means you are supposed to replace that with an appropriate numeral. My my are we hasty or what, but at least we are learning :)

hey some codes are weird..i thought it was one of em.. im just a newborn child in this world.. ..

---

### Post by kittyhawk63 on 2007-03-24
> **HunkieChan said:**
> hey some codes are weird..i thought it was one of em.. im just a newborn child in this world.. ..

HunkieChan,
Did you get your GRUB working the way you wanted? :)
If not, please reply. I can try to give you a solution for your problem.
kh

---

### Post by HunkieChan on 2007-03-24
i disabled it.. it doesnt show at all now.. you can help me with the splash. the one after you put your password in.. how can i change that ?

---

### Post by kittyhawk63 on 2007-03-24
> **HunkieChan said:**
> i disabled it.. it doesnt show at all now.. you can help me with the splash. the one after you put your password in.. how can i change that ?

I'm not sure what you mean by "change that". Do you mean that you want the image changed to a different image? If that is what you mean. you can do a Google search for Linux or Ubuntu Splash screens. There are a number of them available for free. The web sites will give instructions on how to install them.
Or, do you want it to be "removed" completely? I don't know how to do this. If it can be done, someone will know how. Just post it as a separate thread.
kh

---

### Post by HunkieChan on 2007-03-24
thanks bro.. ill try to look for it

---

### Post by kittyhawk63 on 2007-03-25
> **HunkieChan said:**
> thanks bro.. ill try to look for it

You're more than welcome.

---

### Post by HunkieChan on 2007-03-25
thank you

---

