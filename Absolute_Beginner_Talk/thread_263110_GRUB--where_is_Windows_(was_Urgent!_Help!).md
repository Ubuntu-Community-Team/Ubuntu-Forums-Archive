---
title: "GRUB--where is Windows? (was: Urgent! Help!)"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-09-22
Ubuntu was working great on a dual boot laptop with xp.
Have just installed an update in ubuntu and now grub doesnt show xp as an os on boot up and cant connect to net inside ubuntu.
Gonna be in trouble in the morning when family want to use computer...
question - how can i get grub to recognise xp and whats happened to my connection
Using ethernet via cable
Thanks

---

### Post by Brunellus on 2006-09-22
Title changed to reflect support request.  Please use the thread title to give us an idea of the type of problem you have.  Appeals to mercy do not result in useful information.

---

### Post by drifternel on 2006-09-22
ok
thanks for the advice and change of title, appreciated.
will make titles more informative in future...:oops: 
I updated and now have lost the grub screen that recognised windows and also my internet connection within ubuntu
any ideas folks?

---

### Post by bulldog on 2006-09-22
Put this at the end of your GRUB.

gksudo gedit /boot/grub/menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
(hd0,0) 
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

Just fill in your partition and hdd where your windows is.(hd0.0)

---

### Post by drifternel on 2006-09-23
thanks
very new to this..
how do i get the grub list in terminal again, have forgotten the command!

---

### Post by xyz on 2006-09-23
Like bulldog said...in a console, type:
> gksudo gedit /boot/grub/menu.lst

---

### Post by drifternel on 2006-09-23
great - thanks
just need to set xp as default and having trouble working out the number to give as default
heres the menu list

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
default		8

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
# kopt=root=/dev/hda3 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro #single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro #quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro #single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro #quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro #single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

#title		Ubuntu, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin 
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for #
a non-linux OS
# on /dev/hda1
 title		Microsoft Windows XP Professional
 root		(hd0,0)
 savedefault
 makeactive
 chainloader	+1

thanks

---

### Post by Klaidas on 2006-09-23
I wonder: why are there so many threads about disappearing Windows boot?
(No need to "well cuz like kinda windows is closed source so it's good they're gone") 
I mean, is it some (another) update issue?

---

### Post by drifternel on 2006-09-23
everything was fine until i was notified to do an update last night.
On restart instead of just having xp (default) and ubuntu it showed loads of ubuntu options and no xp so yeah for me it was an update issue no doubt

---

### Post by xyz on 2006-09-23
Good question...I was wondering as well!

EDIT: I locked my kernel updates for now.

---

### Post by bulldog on 2006-09-23
> **xyz said:**
> Good question...I was wondering as well!

EDIT: I locked my kernel updates for now.

Chickens..............lol :D

@TS,

great - thanks
just need to set xp as default and having trouble working out the number to give as default
heres the menu list


Well you have all commented out exept 2 that would make 0 and 1 so make the 8 in your menu.lst a 1 and it should start XP by default.

---

### Post by xyz on 2006-09-23
> Chickens..............lol LOL
:D  ;)  and "almost" proud of it!
Got tired of restoring...

---

### Post by drifternel on 2006-09-23
thanks bulldog
didnt know that the uncommented ones didnt count but do now!
No wonder it wasnt working no matter how many times i recounted!!
Ok just one last thing, how do I now make xp top of the list when grub opens - the kids are used to it that way round.
Thanks

---

### Post by bulldog on 2006-09-23
Well I don't know if that's possible to have it on top.

You can set the time out on three seconds [standard =10] and it chooses automaticly XP,so they won't have to use GRUB.

It goes so fast they  haven't a chance to click anything I guess.:D

---

### Post by drifternel on 2006-09-23
It was on top before the update but I have now idea how it got like that in the first place.
Its no big deal so thanks guys for all your help, everythings working fine now.

---

### Post by xpod on 2006-09-23
IM getting me one of those bulldogs when my old staff dies.
He`s on his last legs........he does only have 3 mind you.

Bulldog...you rock:D

---

### Post by bulldog on 2006-09-23
> **xpod said:**
> IM getting me one of those bulldogs when my old staff dies.
He`s on his last legs........he does only have 3 mind you.

Bulldog...you rock:D


Thank You master XPOD.:D 

How is the little technician doing?
She managed to get your second graphical to work at last??

---

### Post by xpod on 2006-09-23
LOL.....havent you heard about my latest adventures with the great utilities cd some kind man sent me.(he feels terrible but i just like to wind him up even though it aint HIS fault)
Lets just say my Kubunto is fine(even without the rage:D )

But alas my poor Ubu\XP died a death and after reinstalling XP with nothing but my dusty old "i386" files again i decided to just wipe it back off and only just gave Ubunto the whole pc as of 2 hours ago:D .

XP can stay put until i stick it somewhere else:-\" 

Kassi was unfortunately sleeping at the time... hence the reason it`s only "half assed" now:biggrin: 

IT`S ALL GOOD AS ALWAYS MATE!!!!

---

### Post by bulldog on 2006-09-23
But alas my poor Ubu\XP died a death and after reinstalling XP with nothing but my dusty old "i386" files again i decided to just wipe it back off and only just gave Ubunto the whole pc as of 2 hours ago .

Think you did a wise decision there.

XP has his good things though,but it takes to much precious space.

---

### Post by xpod on 2006-09-23
AND time, when you aint got a bootable cd:shock: 

I can understand all the folks who have used it for years and years not being able to let go....
I only used it 4 months and not at all really since first getting ubunto but i was just allowing myself to get annoyed at it IF it was`nt on the pc.....
I think im over it now:D 

It aint getting back on this hd.....another yes but not this one!...IF:D

---

### Post by Nytram on 2006-09-23
> **drifternel said:**
> It was on top before the update but I have now idea how it got like that in the first place.
Its no big deal so thanks guys for all your help, everythings working fine now.

when i first installed ubuntu i chose to have windows as the default loader, and on top. i cut and pasted the windows section of menu.lst into the first position, and left the default number as it was (0 i think)

---

