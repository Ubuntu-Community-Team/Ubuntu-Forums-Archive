---
title: "GRUB problem and firefox 2 install help"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-22
I installed some system updates and I now have 2 kernel versions on my GRUB loader.  Is there a way to and should I remove the old one.  Also, I want to install the newest firefox version.  If I download it from mozilla's website I get a tar.gz file.  Is that a package or is it just a compressed file?  How can I install it?

---

### Post by taurus on 2007-02-22
I recommend you keep the older kernel just in case the new one gives you some trouble.  If you remove it, then you would have a dead machine.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Ben Sprinkle on 2007-02-22
Or if you do not want it, look in synaptic at broken/outdated packages. You can remove it there.

---

### Post by louis_nichols on 2007-02-22
It is generally a good idea to keep the original kernel and the latest kernel. The others, you can uninstall.

As for firefox, afaik, in the Ubuntu repos, it is kept up-to-date.
EDIT: typos

---

### Post by oceanspray on 2007-02-22
Hi, a fast question about the GRUB loader: I have three OS's on my computer, Win XP, and Ubuntu on drive 1 and Vista on drive 2, the GRUB interface looks like a plate of spaghetti to me, how can I beautify it?  Mean have four references to Ubuntu and then a reference to Memory Test and lastly a ref to the Windows boot loader, which itself hides an option to either boot Vista or XP...

---

### Post by Matt1632 on 2007-02-22
How do I access the repositories to get the package?

---

### Post by Ben Sprinkle on 2007-02-22
> **oceanspray said:**
> Hi, a fast question about the GRUB loader: I have three OS's on my computer, Win XP, and Ubuntu on drive 1 and Vista on drive 2, the GRUB interface looks like a plate of spaghetti to me, how can I beautify it?  Mean have four references to Ubuntu and then a reference to Memory Test and lastly a ref to the Windows boot loader, which itself hides an option to either boot Vista or XP...

You may want to try GfxBoot. (Maybe called GfxGrub)
There is a howto on this site, just search.

---

### Post by oceanspray on 2007-02-22
Matt, if you're not sure how to go about installing FF, get Automatix, it does it all for you: [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by oceanspray on 2007-02-22
> **Ben Sprinkle said:**
> You may want to try GfxBoot. (Maybe called GfxGrub)
There is a howto on this site, just search.

Thanks!

---

### Post by Maestro23 on 2007-02-22
> **Matt1632 said:**
> How do I access the repositories to get the package?

Use Synaptic(GUI) and search for firefox

Use command-line:

> sudo aptitude install firefox

How to install in Ubuntu:

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by taurus on 2007-02-22
Are you using Dapper or Edgy?

---

### Post by Matt1632 on 2007-02-22
Ok, I found firefox in synaptic, but it's not the 2.0 latest version.  Can I update the repositories?

---

### Post by louis_nichols on 2007-02-22
Grub can use background images to look better. There are such images that can be installed via synaptic. Many are quite nice.

As for the menu, that can be configured by editing the file /boot/grub/menu.lst. Every entry in your boot menu will have at the end of that file an easily recognizable block of parameters. All you need to do to manipulate the order in which they appear at boot is cut and paste to reorder them.

As for the windows boot menu, I'm not sure... don't you enter that by default when you choose to boot to Windows?

---

### Post by taurus on 2007-02-22
Sounds like you are using Dapper.  If you want to run the latest version of firefox, then you need to install it by hand.  This guide will walk you through it.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Matt1632 on 2007-02-22
I'm using dapper.

---

### Post by oceanspray on 2007-02-22
> **louis_nichols said:**
> Grub can use background images to look better. There are such images that can be installed via synaptic. Many are quite nice.

As for the menu, that can be configured by editing the file /boot/grub/menu.lst. Every entry in your boot menu will have at the end of that file an easily recognizable block of parameters. All you need to do to manipulate the order in which they appear at boot is cut and paste to reorder them.

As for the windows boot menu, I'm not sure... don't you enter that by default when you choose to boot to Windows?

Added Ubuntu later and its GRUB loader takes care of business.   Ubuntu boots first, only when I select the Windows/Longhorn loader will the Windows Vista loader show up and it lets me choose between XP and Vista.

HOPE the editing will not mess things up.

---

### Post by Ben Sprinkle on 2007-02-22
> **oceanspray said:**
> Thanks!

No problem.

---

### Post by louis_nichols on 2007-02-22
> **oceanspray said:**
> Added Ubuntu later and its GRUB loader takes care of business.   Ubuntu boots first, only when I select the Windows/Longhorn loader will the Windows Vista loader show up and it lets me choose between XP and Vista.

HOPE the editing will not mess things up.

Oh. Sorry for not mentioning. It is ALWAYS strongly recommended that you make a backup any important file you edit. Just type in terminal

sudo cp /boot/grub/menu.lst /boot/grup/menu.lst.backup

---

### Post by oceanspray on 2007-02-22
> **louis_nichols said:**
> Oh. Sorry for not mentioning. It is ALWAYS strongly recommended that you make a backup any important file you edit. Just type in terminal

sudo cp /boot/grub/menu.lst /boot/grup/menu.lst.backup

Thanks for the warning, did go ahead and it worked out fine, this is what the menu looks like now:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

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
# kopt=root=UUID=5069eec0-ab54-4708-8f40-96c3af0e6c2c ro
# kopt_2_6=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot



### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP, Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1




```

---

### Post by igknighted on 2007-02-22
There's an install script that will install the latest swiftfox on your system... swiftfox is exactly the same as firefox, but custom compiled for your processor type (they are pre-compiled, the script gets the proper one).  I would recommend getting this as it is FF2 but faster.

EDIT: see [www.getswiftfox.com](www.getswiftfox.com)

---

