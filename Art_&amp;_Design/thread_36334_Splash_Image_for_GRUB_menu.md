---
title: "Splash Image for GRUB menu"
date: 2005-05-22
forum: Art &amp; Design
---

### Post by jiyuu0 on 2005-05-22
I've just added this topic

How to display Splash Image for GRUB menu on boot-up?
[http://ubuntuguide.org/#displaysplashimagegrub](http://ubuntuguide.org/#displaysplashimagegrub)

In the e.g. i've used this Splash Image
[http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz](http://frankandjacq.com/ubuntuguide/ubuntu.xpm.gz)

looks familiar?
[img]http://myosc.org/jiyuu0/ubuntu_splash_image.png[/img]

I'm not so good in artwork. Does anyone here have any cool Splash Image?
I would love to replace the e.g. Splash Image with something cooler.

---

### Post by bored2k on 2005-05-22
I downloaded some a while ago, check them out.
[http://bored2k.cjb.net/](http://bored2k.cjb.net/) [there are 28 images in the .rar]

edit - Just browse them all [http://www.schultz-net.dk/grub.html](http://www.schultz-net.dk/grub.html) .

---

### Post by jiyuu0 on 2005-05-23
just test...
unfortunately, their ubuntu's splash image seems a bit too bright
and with white fonts. seems not so nice :(

---

### Post by hammett111 on 2005-05-23
I copied exactly what your link said to do: [http://ubuntuguide.org/#displaysplashimagegrub](http://ubuntuguide.org/#displaysplashimagegrub) and the splash screen only comes up for a sec and then disappears, going back to the text boot!!! Suggestions!!!

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd0,0)/boot/grub/images/ubuntu.xpm.gz

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro console=tty0

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

title		Ubuntu, kernel 2.6.11-1-amd64-k8 Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/sda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.11-1-amd64-k8 Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/sda1 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.11-1-amd64-k8 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-1-amd64-k8 root=/dev/sda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.11-1-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.11-1-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.11-1-amd64-k8 root=/dev/sda1 ro console=tty0 single
initrd		/boot/initrd.img-2.6.11-1-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-k8 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-k8 root=/dev/sda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-k8 root=/dev/sda1 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sda1 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by elsewhere on 2005-05-23
The grub-splashimages package in synaptic will install some splash images, but they're all rather generic.

For kubuntu users, I pulled [this one](http://www.kde-look.org/content/show.php?content=23171) from kde-look.org, looks pretty good and keeps a consistent feel. 

Maybe gnome-look has similar options for ubuntu users ?

Cheers,
KV

---

### Post by bored2k on 2005-05-23
hammet111, I suggest you try installing the grub images with grubconf.

---

### Post by Staesys on 2005-05-24
I have followed all the tutorials and edited the /boot/grub/menu.lst file by hand and using grubconf. The only time I see a splash image is a small sliver that is just big enough to serve as the background for the words while it waits 3 seconds for me to press esc. If I press esc, I see the full background. I then press enter to select the first option and it's all text from then on. Also, if I wait and don't press esc to enter the menu, it goes to the text only boot after that.

Any questions?

Below is my /boot/grub/menu.lst file.

-Paul

```
# Generated by grubconf-0.5.1
default=0
hiddenmenu
timeout=3
splashimage=(hd0,0)/boot/grub/splashimages/grub.xpm.gz

title Ubuntu, kernel 2.6.10-5-386 
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
title Ubuntu, kernel memtest86+ 
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

---

### Post by ceng1984 on 2005-08-14
Staesys,

Try removing the hidden menu item in **[COLOR=Red]Grubconf[/COLOR]**. This should allow you to see the splash screen.

ceng1984

---

