---
title: "changing my grub boot default"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by hyimted on 2006-03-15
hi all -

i installed ubuntu along with winxp ... but i'd like winxp to be the default.  i know i'm supposed to do something with my menu.lst file, but i'm not sure what.  i read that article from the users.bigpond.net site ... but i'm still confused.

it states i'm supposed to change some number value to match where windows xp lies ... but i don't see it in my file?  i've attached a copy of the bottom part of my file for your review.

anyway, any help is appreciated!

ted
[B]
btw, i'm actually posting this from ubuntu ... not xp.  yay!  ;)[/B]

> title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
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
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Adrian on 2006-03-15
At the very top of **/boot/grub/menu.lst**, try adding this line:

```

default 6

```

That should make the 7th entry in the menu the default entry.

---

### Post by aysiu on 2006-03-15
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by hyimted on 2006-03-15
ah...that link helped ... thanks.  couple of other q's before i do this.

1.  if i do this wrong, am i going to bone my whole install?
2.  adrian - shouldn't the default be "6" (since i start counting from zero)?
3.  i just found the default line, it's near the top.  i guess the ## is to comment out that functionality?

thanks again!

---

### Post by Adrian on 2006-03-15
[QUOTE=hyimted]
1.  if i do this wrong, am i going to bone my whole install?
[/QUOTE]
Not likely, but if you want to be safe, make sure to have a livecd nearby. If you make a backup of menu.lst, you can restore it with the help of the livecd.

[QUOTE=hyimted]
2.  adrian - shouldn't the default be "6" (since i start counting from zero)?
[/QUOTE]

Yes. But I wrote that, didn't I? :confused: :confused: :)

[QUOTE=hyimted]
3.  i just found the default line, it's near the top.  i guess the ## is to comment out that functionality?
[/QUOTE]

True. Just remove the ## and change the value.

---

### Post by Mustard on 2006-03-15
[QUOTE=hyimted]ah...that link helped ... thanks.  couple of other q's before i do this.

1.  if i do this wrong, am i going to bone my whole install?
2.  adrian - shouldn't the default be "6" (since i start counting from zero)?
3.  i just found the default line, it's near the top.  i guess the ## is to comment out that functionality?

thanks again![/QUOTE]

1. Just changing the value of default shouldn't bork anything.
2. I count  '5' starting from zero on the above menu.lst *scratches head*
3. Yes.  The hash symbol is used to comment out functionality.

-edit-

Oh, I see..there is one more little one between the linux ones and the windows one. :)

---

### Post by Adrian on 2006-03-15
[QUOTE=Mustard]
2. I count  '5' starting from zero on the above menu.lst *scratches head*
[/QUOTE]

Well, so do I now :)

(since I'm an engineer, maybe learning how to count is a good idea ;) )

Edit: Well, it seems like I could count after all :)

---

### Post by hyimted on 2006-03-15
[QUOTE=Adrian]Yes. But I wrote that, didn't I? :confused: :confused: :)[/QUOTE]oh my bad ... for some reason i thought there was a 7.  ugh ... i'm in the terminal editor right now .... kinda scary!  i'll keep ya posted!  :p

---

### Post by hyimted on 2006-03-15
hmm...no luck with default set to 6.  if someone is supremely bored, would you mind looking at my menu.lst file?  hopefully i attached it correctly.

i'm pretty sure i'm doing everything correct ... but who knows.

edit:  doesn't look like my attachment worked?  anyway, here's the entire file:

[B][INDENT]default 6
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
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
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/INDENT][/B]

---

### Post by aysiu on 2006-03-15
[QUOTE=hyimted]```
**default 6**
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
**default 0**

```[/QUOTE] You have *default* in there twice.

---

### Post by hyimted on 2006-03-15
[QUOTE=aysiu]You have *default* in there twice.[/QUOTE]
[SIZE="5"]doh![/SIZE]  uh..thank god this is the absolute beginner forum.  \\:D/

---

### Post by aysiu on 2006-03-15
Get rid of the first *default 6* and then change the *default 0* to *default 6*.

---

### Post by hyimted on 2006-03-15
[QUOTE=aysiu]Get rid of the first *default 6* and then change the *default 0* to *default 6*.[/QUOTE]welp, that didn't work either.  spacing after the word default doesn't matter does it?  good grief ... this can't be that hard.  but i did notice something right above the default value:
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.  i guess i'll try that next ... since xp has that value in it.

---

### Post by Adrian on 2006-03-15
...or maybe the divider doesn't count as an item (would be logical anyway).
You can try setting **default** to **5** and see what happens...

---

### Post by hyimted on 2006-03-15
no luck setting default to 5 either.

well, i'm certainly at a loss ... it can't be that hard.  thanks for helping me try ... maybe i'll pick this up later.

---

### Post by aysiu on 2006-03-15
When you say "no luck," what does that mean? You boot up and Ubuntu is still the default?

---

### Post by hyimted on 2006-03-15
SUCCESS!  i'm not sure what happened, but i finally got it to work.  the only thing i noticed (and i'm not sure if it matters or not) was that there were a couple of carriage-returns at the very end of the file.  when i edited and deleted the lines, it seemed to fix the problem.

in any case, xp is now the default highlighted menu choice during bootup.  thanks for the help guys ... much appreciated!

---

