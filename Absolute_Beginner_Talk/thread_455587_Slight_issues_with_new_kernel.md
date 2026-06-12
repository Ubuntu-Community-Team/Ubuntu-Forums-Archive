---
title: "Slight issues with new kernel?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-26
After installing the new kernel for Feisty final, my system seems to be rather laggy. 

However, in Grub menu at startup, I don't get any options for choosing an older kernel. Furthermore, no such options are listed in menu.lst .

I think there might have been a problem when Nautilus hung 'cos I made the mistake of trying to drop and drag a file from Nautilus into Vbox. Therefore, I was forced to restart X. 
 
Not sure if that's connected to this issue at all but I thought I'd mention it.

Any way I can try and revert the situation and reinstall the new kernel?

---

### Post by Bachstelze on 2007-05-26
Is the old kernel still here ? 

```
ls /boot
```

---

### Post by Lucifiel on 2007-05-26
> **HymnToLife said:**
> Is the old kernel still here ? 

```
ls /boot
```
lucifiel@lucifiel-desktop:~$ ls -al /boot
total 16948
drwxr-xr-x  3 root root    4096 2007-05-24 19:34 .
drwxr-xr-x 21 root root    4096 2007-05-24 02:53 ..
-rw-r--r--  1 root root  414210 2007-04-15 16:07 abi-2.6.20-15-generic
-rw-r--r--  1 root root   83234 2007-04-15 13:33 config-2.6.20-15-generic
drwxr-xr-x  2 root root    4096 2007-05-24 02:53 grub
-rw-r--r--  1 root root 6952469 2007-05-24 19:34 initrd.img-2.6.20-15-generic
-rw-r--r--  1 root root 7177698 2007-05-24 02:53 initrd.img-2.6.20-15-generic.bak
-rw-r--r--  1 root root   94600 2006-10-20 19:44 memtest86+.bin
-rw-r--r--  1 root root  806942 2007-04-15 16:08 System.map-2.6.20-15-generic
-rw-r--r--  1 root root 1745100 2007-04-15 16:07 vmlinuz-2.6.20-15-generic

Hmmm... strange. I can't find my new kernels anywhere? (edit: it's 27th may where I live, btw. and I reinstalled ubuntu on 24th.)

Would it be possible to restore my backup kernels?

---

### Post by ikonia on 2007-05-26
showus your menu.lst so we can see where your boot options are looking for the kernel.

---

### Post by Lucifiel on 2007-05-26
> **ikonia said:**
> showus your menu.lst so we can see where your boot options are looking for the kernel.

menu.lst :

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=990a6d36-9d0e-49a0-9af3-3bb6e3f47e0a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=990a6d36-9d0e-49a0-9af3-3bb6e3f47e0a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=990a6d36-9d0e-49a0-9af3-3bb6e3f47e0a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by ikonia on 2007-05-26
that does look like your using a "new" kernel.

There is only one kernel in that list, and it matches the one in /boot

Is this not the version your expecting.

---

### Post by Bachstelze on 2007-05-26
Yep, no new kernel here. The 2.6.20-15 is the one the Feisty CD installs...

---

### Post by Lucifiel on 2007-05-26
> **ikonia said:**
> that does look like your using a "new" kernel.

There is only one kernel in that list, and it matches the one in /boot

Is this not the version your expecting.

Well... darnit. 'Cos my system is lagging and I'd like to use the previous kernels for now. Yet, if the new kernels aren't there, what happened to them? O_o;;

---

### Post by Lucifiel on 2007-05-26
> **HymnToLife said:**
> Yep, no new kernel here. The 2.6.20-15 is the one the Feisty CD installs...

Oh crud!

Think I remembered something. I accidentally overwrote the current kernel when I installed Vbox guest additions!!!!

I did that in the Host o/s instead of within vbox!

*smacks her head* 

I'm going to install an older kernel now. Geez!

---

### Post by Lucifiel on 2007-05-26
Sorry for posting so many times with a few minutes.

Does anyone know where I can find the older kernels? Because I can't find them within Synaptic, even with all software sources (except for source code) selected.

---

### Post by ayenack on 2007-05-26
**System>Administration>Synaptic Package Manager** then click **search** and type **linux-image** this will bring up a list of kernels that you can use be careful not to remove your working kernel until you test any kernel you install. This is also a good way to see what kernels you have installed.

Apologies I did not read all of your previous message. oops.

ayenack.

---

### Post by Lucifiel on 2007-05-26
> **ayenack said:**
> **System>Administration>Synaptic Package Manager** then click **search** and type **linux-image** this will bring up a list of kernels that you can use be careful not to remove your working kernel until you test any kernel you install. This si also a good way to see what kernels you have installed.

Apologies I did not read all of your previous message. oops.

ayenack.

All right... think my installed kernels are messed up. 

linux-image-2.6.20-16-generic sounds pretty okay. Btw, the package description reads


You likely do not want to install this package directly. Instead, install
the linux-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.

So, is it still okay to download and install this?


Edit: I found a guide on how to purge and reinstall the kernel.

Does anyone know if these commands still work in Feisty? 

[http://occy.net/node/142](http://occy.net/node/142)

---

### Post by ayenack on 2007-05-26
You should be able to install it with no probs just don't remove the kernel that is working now until you know for sure that the linux-image-2.6.20-16-generic or the meta one works. I don't want to say that this will defo work and not mess up your system but I've done this numerous times and always been able to boot back to the old kernel if anything goes wrong. When you reboot select it and see if it will boot ok. You may well be kicked down to the command line because of xorg.conf config is not set up correctly for that kernel. Normally because of the graphics driver is not configured for that kernel. If it doesn't work you should be able to restart your system and and boot using the old kernel. Might be an idea to backup any important data first just to be safe.

You might also try using Update Manager to see if it gives you the option to upgrade the kernel, might do.

ayenack.

---

### Post by ayenack on 2007-05-26
> [I]Edit: I found a guide on how to purge and reinstall the kernel.

Does anyone know if these commands still work in Feisty?

[http://occy.net/node/142](http://occy.net/node/142)
[/I]

As far as I can tell this is exactly the same as using Synaptic but doing it at the command line. If I were you I would not remove the old kernel until I know the new one works.

ayenack.

---

### Post by Lucifiel on 2007-05-26
> **ayenack said:**
> You should be able to install it with no probs just don't remove the kernel that is working now until you know for sure that the linux-image-2.6.20-16-generic or the meta one works. I don't want to say that this will defo work and not mess up your system but I've done this numerous times and always been able to boot back to the old kernel if anything goes wrong. When you reboot select it and see if it will boot ok. You may well be kicked down to the command line because of xorg.conf config is not set up correctly for that kernel. Normally because of the graphics driver is not configured for that kernel. If it doesn't work you should be able to restart your system and and boot using the old kernel. Might be an idea to backup any important data first just to be safe.

You might also try using Update Manager to see if it gives you the option to upgrade the kernel, might do.

ayenack.

Eh, it's okay. My home is on a different partition. So, I doubt hosing my Ubuntu installation would destroy any of that data. Plus, I have my entire /apt/cache backed up. 

Ugh... can't I just boot into livecd and copy the kernels over to /boot ? 

Update manager doesn't give anything kernel-related. Okay, I'll install and reboot now.

---

### Post by ayenack on 2007-05-26
You can use the live CD to rescue your system. Put it in the drive and type rescue at command line before it boots into the live CD. Follow instructions and hope for the best.

ayenack.

---

### Post by Lucifiel on 2007-05-26
> **ayenack said:**
> You can use the live CD to rescue your system. Put it in the drive and type rescue at command line before it boots into the live CD. Follow instructions and hope for the best.

ayenack.

Aha!

Thanks for that. ;)

I think this sounds like a better solution than trying a new kernel.

---

### Post by ayenack on 2007-05-26
No probs. Just noticed how many beans you've got 570 that's a hell of a lot for three months:grin:

Best of luck. ayenack.

---

### Post by Lucifiel on 2007-05-26
> **ayenack said:**
> No probs. Just noticed how many beans you've got 570 that's a hell of a lot for three months:grin:

Best of luck. ayenack.

Uhhh wait... btw, how the heck do I reach command line before I boot into the livecd??? I'm in the livecd now but I tried pressing e and nothing happened, and I got the boot list? 

Sorry, getting a little frustrated now. :( 

Thanks. :)

---

### Post by Lucifiel on 2007-05-26
Oh and after I type rescue , what am I supposed to do? 'Cos wouldn't I have to type a whole list of commands after that?

---

### Post by jerrylamos on 2007-05-26
Do you have the CD Live from the Feisty release?  If so, the original Feisty release kernel is there.

---

### Post by Lucifiel on 2007-05-26
> **jerrylamos said:**
> Do you have the CD Live from the Feisty release?  If so, the original Feisty release kernel is there.

Oh, so I can just copy the original kernel over, huh?

Okay then. Yes, I've the Live CD. :)


Man, my only hope is that the Virtualbox Guest Additions doesn't mess up my system any further. :(

---

### Post by Lucifiel on 2007-05-26
Errrr... guys, which files am I supposed to copy ? initrg .bak and ?????

---

### Post by ayenack on 2007-05-26
I was just about to crash. When you put the live CD in the CD drive and the system starts to boot from it, it give you a few option before it actually boots. The first thing you need to do is tap the arrow key's up and down this will stop it auto booting. Then if you look down at the bottom of the screen you will see press F1 for languages (I think) and so on, anyway there are more options to chose from I think the one you need is **MORE OPTIONS** F6 (I think it is) you'll see it at the bottom of the page, hit the Function key it tells you to and this will bring some white writing up on the page you need to delete all the writing using the delete key and type rescue, then hit the return key. That's it. If you do a google search there should be info on this and what you need to do.

I'm going to crash now so hope all goes well for you will check back later to see if you need any help. L8R's
ayenack.

BTW copying the kernel image over from the live CD is just the same as downloading it and installing it from Synaptic.
Note: rescue is not the same as copying the kernel it will try to rescue your system.

---

### Post by Lucifiel on 2007-05-26
> **ayenack said:**
> I was just about to crash. When you put the live CD in the CD drive and the system starts to boot from it, it give you a few option before it actually boots. The first thing you need to do is tap the arrow key's up and down this will stop it auto booting. Then if you look down at the bottom of the screen you will see press F1 for languages (I think) and so on, anyway there are more options to chose from I think the one you need is **MORE OPTIONS** F6 (I think it is) you'll see it at the bottom of the page, hit the Function key it tells you to and this will bring some white writing up on the page you need to delete all the writing using the delete key and type rescue, then hit the return key. That's it. If you do a google search there should be info on this and what you need to do.

I'm going to crash now so hope all goes well for you will check back later to see if you need any help. L8R's
ayenack.

BTW copying the kernel image over from the live CD is just the same as downloading it and installing it from Synaptic.
Note: rescue is not the same as copying the kernel it will try to rescue your system.

*sighs* I tried selecting the option "Boot from hard disk" with F6 "rescue". But nothing seems to  happen? ?__? 'Cos selecting the first option "Start Ubuntu Or install" and then typing "rescue" would result in a kernel panic.


Okay, thank you. :)

---

### Post by Lucifiel on 2007-05-26
*Sighs* Why do I think that "rescue" will not work and my only option is to reinstall Ubuntu??

That will make it what? my 7th to 8th time installing Ubuntu with just 2 months.

---

### Post by Lucifiel on 2007-05-26
... ...

Does anyone know the proper procedure for using command "rescue" in Ubuntu F6 options? Which selection am I supposed to choose? 


Geez...

---

### Post by ayenack on 2007-05-27
It'll take an age and about a hundred post to try to explain your options when you rescue your system. So I typed this into google **how to rescue an ubuntu system** and it came up with [these pages]("http://www.google.co.uk/search?hl=en&q=how+to+rescue+an+ubuntu+system&btnG=Google+Search&meta=") I suggest you take a look at [this one]("http://codeidol.com/unix/ubuntu/Administration/Rescue-an-Unbootable-System/").

ayenack.

---

### Post by Lucifiel on 2007-05-27
> **ayenack said:**
> It'll take an age and about a hundred post to try to explain your options when you rescue your system. So I typed this into google **how to rescue an ubuntu system** and it came up with [these pages]("http://www.google.co.uk/search?hl=en&q=how+to+rescue+an+ubuntu+system&btnG=Google+Search&meta=") I suggest you take a look at [this one]("http://codeidol.com/unix/ubuntu/Administration/Rescue-an-Unbootable-System/").

ayenack.

Uh oh, the Feisty Fawn livecd doesn't appear to have this option when you boot up into it.

Hmmm... I'll probably have to find out how to access this mode and how to make it work, then.

Thank you for the links! :)

---

### Post by Lucifiel on 2007-05-27
Well, I sorta decided not to use rescue function for now, since I was unable to find it.

I have since then done a reinstall and learnt how to use a bash script to automate my installations. :)

However, I will definitely setup Vbox again and try messing up my Vbox installation. Then, I'll give the rescue function a try. =D

---

### Post by ayenack on 2007-05-27
Before you install V Box again take a look at this [site]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html") it tells you what to do before you install V Box and the best way to go about installing it. May solve the problems you've encountered after installing it previously.

Best of luck. ayenack.

---

