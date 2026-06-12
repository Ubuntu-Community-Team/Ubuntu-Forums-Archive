---
title: "[SOLVED] Old kernels never die?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-08-30
Every time Ubuntu decides to update it's kernel, I get 2 new lines in the Grub menu.lst & the PC boots to Memtest 86 instead of normal family default XP.

Then I need to reboot manually, remember how to get to menu.lst as root & increment the default line by 2.
Currently I have generic & recovery mode versions of:
2.6.20-16
2.6.17-12
2.6.17-11
2.6.17-10

Is this normal?

Why such a dumb process? (or is that a dumb question?)

Do I need to keep some or all of the old kernels or not?
How many?

How do I get rid of the ones I don't need?
Preferably by a foolproof GUI method!

Thanks inadvance for any help!

---

### Post by mckryptyk on 2007-08-30
1) You will need to modify grub to prevent XP from disappering.

2) Yes you can delete certain things safely.

Why don't we start with number one:

Please post your grub.conf file here. Use Applications -> Accessories -> Terminal in the menu.

```
sudo cp /boot/grub/menu.lst ~/Desktop/menu.lst
```

Cheers.

---

### Post by Obor on 2007-08-30
I usually remove the old kernels once I make sure that the new one works ok. All you have to do is open synaptic and search for **linux-image** and uninstall all the old ones (make sure that you keep the one that works/latest one). 
This will automatically remove them from your GRUB as well. Plus it will free up some space as each kernel is about 80MB.

---

### Post by stevebakerj on 2007-08-30
> **mckryptyk said:**
> 1) You will need to modify grub to prevent XP from disappering. 

or you can find this set of lines in your menu.lst 

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

and un # (hash) the # updatedefaultentry=false

and to get rid of old Kernels just delete them in Adept or Synaptic and that will update your grub for you.

---

### Post by mckryptyk on 2007-08-31
> Talking Re: Old kernels never die?
Quote:
Originally Posted by mckryptyk View Post
1) You will need to modify grub to prevent XP from disappering.
or you can find this set of lines in your menu.lst

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

and un # (hash) the # updatedefaultentry=false

and to get rid of old Kernels just delete them in Adept or Synaptic and that will update your grub for you.
__________________
Steve


That is modifying grub's boot list (menu.lst) from making XP disappear.
Maybe I just wasn't clear. :confused:


However, he should modify the end of /boot/grub/menu.lst and add this instead:

### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows 95/98/NT/2000/XP
root          (hd0,0)
makeactive
chainloader   +1

This will let grub "auto-update" without modifying his windows boot settings.

Cheers.

---

### Post by mikewhatever on 2007-08-31
> **2CV67 said:**
> Every time Ubuntu decides to update it's kernel, I get 2 new lines in the Grub menu.lst & the PC boots to Memtest 86 instead of normal family default XP.

Then I need to reboot manually, remember how to get to menu.lst as root & increment the default line by 2.
Currently I have generic & recovery mode versions of:
2.6.20-16
2.6.17-12
2.6.17-11
2.6.17-10

Is this normal?

Why such a dumb process? (or is that a dumb question?)

Do I need to keep some or all of the old kernels or not?
How many?

How do I get rid of the ones I don't need?
Preferably by a foolproof GUI method!

Thanks inadvance for any help!

If the newest kernel works and you do not need the older ones, simply remove them. Open Synaptic and search for kernel-image, pick the kernels you do not want, right click and mark for removal. That should also update grub menu.

---

### Post by Seisen on 2007-08-31
I recommend that you keep at least the current version of your kernel and the previous version in case you run into problems with the new one. Trust me it might sound stupid but does come in handy.

---

### Post by 2CV67 on 2007-09-01
Thanks, guys, for all your help & suggestions.

I now understand (I think...)
1. I should probably keep the last good kernel as well as the current one.
2. I can safely delete old kernels via Synapt. I tried this by deleting the oldest one (2.6.17-10). It disappeared from menu.lst & from the boot page menu, without affecting the default option number, so I still had to reajust that manually. If I had deleted it as soon as the new kernel arrived, the result would have been OK.
3. I don't have to do anything about the "recovery mode" kernels listed - they get deleted with the "generic" kernels.
4. The kernels are called "linux-image" in synapt, not "kernel" or "kernel-image". I guess I would never have found them without help!
5. I can probably fiddle with menu.lst so as to keep the default boot to XP (essential for other family members at the moment) even when new kernels arrive but I have not tried that yet.
6. I don't think there is a way for incoming new kernels to delete last-but-one kernels automatically - is there?

I am posting below, my current "menu.lst" after deleting 2.6.17-10 & adjusting the default to 8.

Thanks again for those suggestions, and any future ones!

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
timeout		3

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
# kopt=root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mckryptyk on 2007-09-03
Here is what my menu.lst looks like compare it to yours:

[ATTACH]42445[/ATTACH] (My menu.lst)
**In menu.lst, Do not change any of the UUID settings as those are unique to your computer.

I have included some commands below to clean up your kernels once you have configured your menu.lst by comparing it to the one I've uploaded.

I have already tested these on my own machine (the one I'm posting on) before posting them here.

Below will explain what the command does first and further down is the command. 

1) This piece of code below will update your packages from the repos (so your computer will know what's new)

2) Remove all kernels and kernel-related while running (It is okay to do this just do not reboot until complete)

3) Reinstall the latest kernel, it's headers and restricted-modules needed for nvidia-glx or ati

4) Update and Upgrade any new packages from the repos and configure them for the new kernel if needed.

** Make sure not to reboot/power-down while doing this **

Copy this into terminal: 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
sudo apt-get update && sudo apt-get remove --purge linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-generic linux-headers* linux-image* linux-restricted-modules* && sudo apt-get install linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-generic && sudo apt-get update && sudo apt-get upgrade
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5) After all this is done, If you use nvidia-glx/nvidia-glx-new please type what's below to reinstall it for the new kernel. If you use Ati/fglrx please reinstall it however you did previously before you reboot. 

```
sudo apt-get install nvidia-glx
``` (I use Nvidia so it's what I'm familiar with.)

Let me know if you have any problems and I'll help you with them.

Cheers.

---

### Post by beefcurry on 2007-09-03
Be best to leave at least the last working one. I've had troubles with newer kernels sometimes.

---

### Post by mckryptyk on 2007-09-03
Yes if you leave out the graphics module, then be sure to change the xorg setting so it will be graphic when you reboot.

This makes a backup before you change settings.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This is to change settings.
```
sudo gedit /etc/X11/xorg.conf
```

Now go down to where it says: (Yours will look a bit different)

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

** And change "nvidia" to "nv"

** If you have Ati then change from "flgrx" to "ati"

Now save and reboot.

Cheers.

Note you will have to reinstall your closed source-graphics driver afterwards, but this will  make sure you can do a graphical reboot.

Cheers.

---

### Post by OrangeCrate on 2007-09-06
Posts above refer to marking for removal. When deleting, should a person mark for removal, or mark for complete removal? If you go the complete removal route, does removing an old kernel affect a newer version?

---

### Post by tgalati4 on 2007-09-06
Set your timeout to 60 seconds from 3 seconds.  This way, an impatient Windows user will be staring at a screen with kernel-linuz-386 gibberish and see Windows and select it with the down arrow key.

---

### Post by A$h X on 2007-09-06
You can just move the windows entry in menu.lst to above the linux kernel entries and make it default so it's auto-highlighted. I recommend changing the timeout to 15 secs so you can choose ubuntu without rushing. (Just to keep things pretty-looking, move the divider line to underneath windows so it reads correctly).

---

### Post by 2CV67 on 2007-09-06
Thanks for all those comments & suggestions, which I have not followed up yet.

I want to avoid digging too deeply in stuff I don't understand.

I intend to keep my 3-second timeout - Starting up is slow enough without adding unnecessary delays & I want XP users to see nothing long enough to worry them. 3 seconds is plenty for me.

The idea of shifting XP to the top of the list & setting default to 0 appleals to me.
Presumably XP would always be default boot then & latest Ubuntu would always be 1 click down?
Older Ubuntus would be further down & could be left or deleted without affecting anything else?

Is that right?

Would I need to modify menu.lst as below, or what? (bear in mind I am not competent in this stuff, I have not understood chainloader + 1 etc etc...).

Thanks!

Tentative:

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP dition familiale
root (hd0,0)
savedefault
makeactive
chainloader +1

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.17-12-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd /boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd /boot/initrd.img-2.6.17-12-generic

title Ubuntu, kernel 2.6.17-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd /boot/initrd.img-2.6.17-11-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by A$h X on 2007-09-06
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```

Put that above the ## ## End Default Options #### line, and your all set. Also if you don't want to uninstall the older kernels, just comment them out by putting #### in front and after. Bear in mind kernel updates will wipe this from menu.lst, so you'll have to add them again after updating.

---

### Post by por100pre1 on 2007-09-06
This may sound like a dumb question but, can't you just uninstall the oldest kernel using Synaptic?

---

### Post by 2CV67 on 2007-09-06
por100pre1: Yes I can just delete old kernels by Synapt. I didn't know that at first, but found out by post #8 I think.

Now I am just looking at ways to tidy it up so it stays working even if I forget to fiddle with it.

I think a system which fails to boot after an automatic update is not a very good system!

Don't you?

Thanks again.

---

### Post by por100pre1 on 2007-09-06
> **2CV67 said:**
> por100pre1: Yes I can just delete old kernels by Synapt. I didn't know that at first, but found out by post #8 I think.

Now I am just looking at ways to tidy it up so it stays working even if I forget to fiddle with it.

I think a system which fails to boot after an automatic update is not a very good system!

Don't you?

Thanks again.

I know how you feel. This recent update caused a lot of trouble to many users. Those issues can be minimized by avoiding programs like Envy, Automatix, and by avoiding external repositories and packages. Of course these updates are not 100% error proof IMHO. :-k

---

### Post by rsambuca on 2007-09-06
There is a line in your menu.lst that says "howmany=all".  Change it to howmany=1 and it will only show the latest kernel.  It should then keep booting to whatever your previous boot option was.

grub was designed to boot to the newest kernel, which if you think about it, is probably right.  Just because you want to set it to boot to another OS is not grub's fault!

---

### Post by angrykeyboarder on 2007-09-06
Dang...

I can't delete..

:(

---

### Post by angrykeyboarder on 2007-09-06
[COLOR=Silver]I replied by mistake in the wrong place. 

Let's try this again..[/COLOR]

I had to re-read your quote about 5 times before I figured out that you had attributed some of it to yourself when in fact it wasn't all yours.

Now that I have that straight...

Should one do both or just what you suggest instead?

---

### Post by rsambuca on 2007-09-06
> **angrykeyboarder said:**
> [COLOR=Silver]I replied by mistake in the wrong place. 

Let's try this again..[/COLOR]

I had to re-read your quote about 5 times before I figured out that you had attributed some of it to yourself when in fact it wasn't all yours.

Now that I have that straight...

Should one do both or just what you suggest instead?

To whom and to what are you referring???

---

### Post by por100pre1 on 2007-09-06
> **rsambuca said:**
> To whom and to what are you referring???

I'm asking myself the same question. I think this is about helping others, not about personal recognition.

---

### Post by 2CV67 on 2007-09-22
Thanks for all those comments.

I have been away from this item for a couple of weeks but would now like to tidy it up once & for all, as simply as possible. 

Yes, I agree the default arrangement ensures booting from the latest Linux kernel & this is logical, but it does not suit my PC where 5 users out of 6 need to boot to XP automatically.

My over-riding concern is to avoid damaging grub & not being able to boot at all, so I would like to avoid some of the more complicated suggestions…

I am attracted by the first part of A$h X’s suggestion in post 16:

> **A$h X said:**
> ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```

Put that above the ## ## End Default Options #### line, and your all set.

Will this result in:
1.	XP being at the top of the grub page & staying the default boot whatever Linux kernel updates arrive
2.	The latest Linux kernel always being 2 clicks down
3.	Older kernels being further down
4.	Even older kernels can be deleted (or not) using APT with no need to revise menu.lst

If so, I will do it.

Presumably I need to set menu.lst “default” to 0 for this?

Can I be reassured 100%  where I should add & remove the changes ? (I have read the blurb in menu.lst several times, but still don’t understand what will & what will not be “modified by the debian update-grub script except for the default options below”…)

Will this tentative version below be OK?

# menu.lst - See: grub(8), info grub, update-grub(8) 
# grub-install(8), grub-floppy(8), 
# grub-md5-crypt, /usr/share/doc/grub 
# and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default 0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout 3 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
#hiddenmenu 

# Pretty colours 
#color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line) and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title Windows 95/98/NT/2000 
# root (hd0,0) 
# makeactive 
# chainloader +1 
# 
# title Linux 
# root (hd0,1) 
# kernel /vmlinuz root=/dev/hda2 ro 
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
## kopt_2_6_8=root=/dev/hdc1 ro 
## kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,2) 

## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
## alternative=false 
# alternative=true 

## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
## lockalternative=false 
# lockalternative=false 

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 

## should update-grub lock old automagic boot options 
## e.g. lockold=false 
## lockold=true 
# lockold=false 

## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 

## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
## altoptions=(recovery) single 
# altoptions=(recovery mode) single 

## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
## howmany=7 
# howmany=all 

## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
## memtest86=false 
# memtest86=true 

## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 

# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/hda1 
title Microsoft Windows XP Edition familiale 
root (hd0,0) 
savedefault 
makeactive 
chainloader +1 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title Other operating systems: 
root 

## ## End Default Options ## 

title Ubuntu, kernel 2.6.20-16-generic 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash 
initrd /boot/initrd.img-2.6.20-16-generic 
quiet 
savedefault 

title Ubuntu, kernel 2.6.20-16-generic (recovery mode) 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single 
initrd /boot/initrd.img-2.6.20-16-generic 

title Ubuntu, kernel 2.6.17-12-generic 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash 
initrd /boot/initrd.img-2.6.17-12-generic 
quiet 
savedefault 

title Ubuntu, kernel 2.6.17-12-generic (recovery mode) 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single 
initrd /boot/initrd.img-2.6.17-12-generic 

title Ubuntu, memtest86+ 
root (hd0,2) 
kernel /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by 2CV67 on 2007-09-27
Well I though that was OK until the first kernel update arrived & it wiped out the "XP & other systems" lines from the boot menu!

So I have gone back to the original menu.lst for the moment.

Did I just put the "XP & other sytems" lines in the wrong place, or is it impossible to have them at the top & not wiped out by updates?

---

### Post by rsambuca on 2007-09-27
You just put them in the wrong place.  In order for them to be left untouched after grub updates, you must place the information after the "### END DEBIAN AUTOMAGIC KERNELS LIST"

---

### Post by mcduck on 2007-09-27
> **rsambuca said:**
> You just put them in the wrong place.  In order for them to be left untouched after grub updates, you must place the information after the "### END DEBIAN AUTOMAGIC KERNELS LIST"

Or before the automagick section. Both work just as well. As long as it's not inside the Automagick section (as that gets rewritten during kernel updates).
```

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Edition familiale
root (hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu, kernel 2.6.17-12-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro quiet splash
initrd /boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-12-generic root=UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 ro single
initrd /boot/initrd.img-2.6.17-12-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by 2CV67 on 2007-09-27
Thanks guys!

I assume (dangerous!) that if I put them before "end of debian" then I will still be unable to default-boot to XP  without rewriting menu.lst every time a kernel update arrives (original & current condition).

I HOPE (from what mcduck says) that if I put them before automagick then that will let me keep XP as default with no need to rewrite menu.lst & no urgency to tidy up old kernels as soon as new ones arrive?

Looks feasible.

I will try it.

Thanks again!

---

### Post by mcduck on 2007-09-27
> **2CV67 said:**
> Thanks guys!

I assume (dangerous!) that if I put them before "end of debian" then I will still be unable to default-boot to XP  without rewriting menu.lst every time a kernel update arrives (original & current condition).

I HOPE (from what mcduck says) that if I put them before automagick then that will let me keep XP as default with no need to rewrite menu.lst & no urgency to tidy up old kernels as soon as new ones arrive?

Looks feasible.

I will try it.

Thanks again!

Yes, that's how it works.

You can also change the "# howmany=all" under default options to "# howmany=2" to get a cleaner grub menu with only 2 kernel versions displayed. That might be nice if you don't uninstall old kernels too often. (I usually remove the old one after couple of days running on the new kernel version without problems).

In the end the menu.list is very well documented inside the file itself, if you just spend some time and read the file through..Pretty much everything you can do with Grub menu is explained in the comments of the file ;)

---

### Post by 2CV67 on 2007-09-27
Yes, I moved the "Other OS & XP" lines to above "Begin Automagic.." & it now works as I want:
Boots automatically to XP, with latest Linux one-click down & older Linuxes below.

I really believe it will stay that way after the next update, leaving me to wipe off oldest kernels with APT whenever I feel like it, without having to coordinate changes in menu.lst.
But I will wait to see that before I [RESOLVED] it!

You mention that it is well documented inside the file itself:
Believe me I have spent a long time wading through that file, but as a user of the "Absolute Beginners" forum, I am quite unable to work out what it all means.
Certainly not with enough confidence to risk making changes which could mean I could not boot to either Ubuntu or Windows!

I think one of the biggest obstacles for Ubuntu is realizing how obscure & it can all appear to a Linux novice, even with years of Windows, Fortran, Basic etc etc.

This forum is one of the best facets of Ubuntu.

Thanks for all the help!

---

### Post by 2CV67 on 2008-01-10
Just updated to Gutsy & new kernel arrived at the top of the Ubuntu pile, one click down from XP with older kernels below - exactly as I hoped!  :)

This is the right solution for my PC with lots of "dumb" XP users plus me  :cool:

Thanks for all the help!

---

