---
title: "problems with menu.lst file"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by path_finder on 2007-09-24
Hi eveyone,

I have edited my menu.lst file to change the splash image. But now it says
"Failed to read splash image ((hd0,3)/boot/Ubuntusplash.xpm.gz)
Press any key to continue .... "

Please help me, I have spent days on this thing!

---

### Post by Kingsley on 2007-09-24
Did you follow some guide? If you did, look over it again and make sure you didn't screw up any steps.

---

### Post by bobplano on 2007-09-24
is the splash image supposed to be compressed? i can't find it in the menu file but that's odd if it's supposed to be. anyway you can just fix it for now with the live cd and go back and tinker later. if you don't know how to fix it)back to the original just post back here.

---

### Post by Adramelech on 2007-09-24
If you are sure thats the path to the image, then the only thing that can be wrong is the (hd0,3).

Check your ubuntu partition number.

Check in menu.lst the the ubuntu boot entry

---

### Post by path_finder on 2007-09-25
Yes I gziped it after saving as a .xpm file. I tried this even with two color images (just black and white).
In botom of the menu.lst file says my root is in (hd0,3).
If could help..!

---

### Post by alienexplorers on 2007-09-25
Can you please list your menu.lst file.....

---

### Post by por100pre1 on 2007-09-25
```
locate Ubuntusplash.xpm.gz
```

post the results...

```
cat /boot/grub/menu.lst
```

post this too...

---

### Post by path_finder on 2007-09-25
I am attaching copy of my menu.lst file with this.

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
default		3
splashimage= (hd0,3)/boot/debsplash.xpm.gz
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

 #Pretty colours
#color           black/brown                       blink-yellow/black

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
# kopt=root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by path_finder on 2007-09-25
result for the -cat /boot/grub/menu.lst -  was my menu.lst file and i have posted that.

result for the -locate Ubuntusplash.xpm.gz-   was - /boot/grub/Ubuntusplash.xpm.gz -


( i added those "  -  "  to separate the result from command.

---

### Post by por100pre1 on 2007-09-25
> **path_finder said:**
> I am attaching copy of my menu.lst file with this.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

[COLOR="SeaGreen"]splashimage (hd0,3)/boot/grub/Ubuntusplash.xpm.gz[/COLOR]
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3
[COLOR="Red"]splashimage= (hd0,3)/boot/debsplash.xpm.gz[/COLOR]
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

 #Pretty colours
#color           black/brown                       blink-yellow/black

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
# kopt=root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Sorry for the delay, I was busy. There's the necessary change, shown in red and green.

Remove the red line, add the green one.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

```
sudo gedit /boot/grub/menu.lst
```

and make the change.

---

### Post by path_finder on 2007-09-25
Thank you so much for helping me like this. But the problem still remains. Now my menu.lst file is like this. Also though i changed fore ground back ground colors, it dosent change itself.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
splashimage (hd0,3)/boot/grub/debsplash.xpm.gz
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

 #Pretty colours
#color           black/brown                       blink-yellow/black

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
# kopt=root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=931c8890-f492-4e79-b487-7359464bfb31 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by path_finder on 2007-10-01
Extremely sorry for the long delay, I am having a dialup connection. someitimes its not working.
problem still remains. what could be the problem. my linux root partiition is not a primary partion. Is it a problem?

Thanks !

---

### Post by eph1973 on 2007-10-01
You have:

```
 splashimage (hd0,3)/boot/grub/debsplash.xpm.gz
```

When I installed grub-splashimages, it put them in the directory /boot/grub/splashimages

So you should try:
```
splashimage (hd0,3)/boot/grub/splashimages/debsplash.xpm.gz
```

---

### Post by Martje_001 on 2007-10-01
Is grub installed on the same partition as ubuntu? Then you can remove (hd0,3)

---

### Post by eph1973 on 2007-10-01
Also, since they are .gz, you may want to try to unzip them to say, your desktop then go back to the terminal and type:

```
sudo mv ~/Desktop/*.xpm /boot/grub/splashimages
```Then change that line to:

```
splashimage (hd0,3)/boot/grub/splashimages/debsplash.xpm
```

---

### Post by distroman on 2007-10-01
Also you could have a look at the following link if you didn't already, have worked well for me in the past.
[https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4](https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4)

---

