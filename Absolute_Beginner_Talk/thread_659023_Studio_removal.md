---
title: "Studio removal"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-01-05
Yesterday I was looking for help installing Studio, today I would like help removing it completely, returning to a dual boot on two drives.
I have looked through Add/remove and Synaptic and all I can find is individual files, not the complete install.
I have a feeling it's so interleaved it might be simpler to totally remove and start again?

---

### Post by Ptero-4 on 2008-01-05
It's AFAIK a metapackage, something like ubuntustudio-desktop. Look for it and remove it and then add ubuntu-desktop.

---

### Post by newbeeman on 2008-01-05
> **Ptero-4 said:**
> It's AFAIK a metapackage, something like ubuntustudio-desktop. Look for it and remove it and then add ubuntu-desktop.

Please explain "AFAIK" 
Tried adding ubuntu-desktop, get a "Depends-Ubuntu sounds but it is not going to be installed.
Looking through your suggestions hasn't made any difference to the screen display.
Comments, please.

---

### Post by aktiwers on 2008-01-05
```
sudo apt-get remove ubuntustudio*
```

Should remove it.

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> ```
sudo apt-get remove ubuntustudio*
```

Should remove it.
Nope!
As I said before, there is so much studio stuff it will be impossible to get back to a 'clean' Ubuntu, it's now forcing a Disc check when I boot into Win.
How about I uninstall and do a clean again. I can restore to a previous Win, find my second drive again, as win can't see my D:\,  then format and re-install. Means a lot of work, but seems to be the only answer I can think of.
How do I uninstall Ubuntu?

---

### Post by aktiwers on 2008-01-05
Did you install Ubuntu studio packages ontop of ubuntu?
Then the command will remove it! The star(*) means all packages with ubuntustudio in it. More precise :

> 
 ubuntustudio-graphics
 ubuntustudio-screensaver 
 ubuntustudiolauncher 
 ubuntustudio-audio-plugins
 ubuntustudio-video 
 ubuntustudio-gdm-theme 
 ubuntustudio-menu
 ubuntustudio-look 
 ubuntustudio-sounds 
 ubuntustudio-artwork
 ubuntustudio-desktop 
 ubuntustudio-theme
 ubuntustudio-audio 
 ubuntustudio-wallpapers
 usplash-theme-ubuntustudio
 ubuntustudio-default-settings
 ubuntustudio-icon-theme 


Which should be all packages?

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> Did you install Ubuntu studio packages ontop of ubuntu?
Then the command will remove it! The star(*) means all packages with ubuntustudio in it.
Which should be all packages?

Correct, my error missed the *.
Now I seem to have 'All' of the sound and video programs installed!!
Can you help me clean up Grub?
During the reboot I have 7 OS choices!! I would like to get back to the original ways of booting.

---

### Post by aktiwers on 2008-01-05
Sound and video should be these packages:
 ubuntustudio-audio 
 ubuntustudio-audio-plugins
 ubuntustudio-video 

So if they are not already removed try:
```
sudo apt-get remove   ubuntustudio-video   ubuntustudio-audio-plugins  ubuntustudio-audio 
```

Or try 
```
sudo apt-get purge ubuntustudio*
```

Now post the output of:
```
cat /boot/grub/menu.lst
```

And tell me what options you would like to have at bootup :)

---

### Post by newbeeman on 2008-01-05
[QUOTE=aktiwers;4077857
Or try 
```
sudo apt-get purge ubuntustudio*
```

Now post the output of:
```
cat /boot/grub/menu.lst
```

And tell me what options you would like to have at bootup :)[/QUOTE]

I have 7 choices. The top 3 were added by Studio and are superfluous by my thinking.

---

### Post by aktiwers on 2008-01-05
I need everything in that file. 
You can copy from terminal by right-clicking and picking Copy.

Or do it like this:
```
gedit /boot/grub/menu.lst
```

And paste everything from that text document.

Did you get completely rid of the Studio packages now?

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> I need everything in that file. 
You can copy from terminal by right-clicking and picking Copy.
Or do it like this:
```
gedit /boot/grub/menu.lst
```
And paste everything from that text document.
Did you get completely rid of the Studio packages now?

Yes, got rid of Studio.
Here are the results of paste.

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
# kopt=root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by aktiwers on 2008-01-05
Ok.. now type:
```
gksudo gedit /boot/grub/menu.lst
```And find this place:

>  ## ## End Default Options ##

[COLOR=Red] title        Ubuntu 7.10, kernel 2.6.22-14-rt
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-rt
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro single
initrd        /boot/initrd.img-2.6.22-14-rt[/COLOR] 

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LISTNow delete the  red ones.

And save the file.

Are you sure you had 7 entrys? 
I only see 6. Well when you are done with this you should have 4.

_like this:_
Ubuntu
Ubuntu (recovery mode)
Memtest 
Windows

Let me know if thats what you planed.

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> Ok.. now type:
```
gksudo gedit /boot/grub/menu.lst
```And find this place:

Now delete the  red ones.
And save the file.
Are you sure you had 7 entrys? 
I only see 6. Well when you are done with this you should have 4.
_like this:_
Ubuntu
Ubuntu (recovery mode)
Memtest 
Windows
Let me know if thats what you planed.


Sorry, didn't fix the problem. Did as you suggested, tried re-booting...twice. Still got an extra 3 lines above the ones I need.
Here is a paste of the file.

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
# kopt=root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=97c71a9e-a953-4d71-942e-967a478c8000 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by aktiwers on 2008-01-05
Thats strange..  can you tell me what options you have on boot?

I would think it looked _like this:_
Ubuntu
Ubuntu (recovery mode)
Memtest 
Windows

How does it look now?

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> Thats strange..  can you tell me what options you have on boot?
I would think it looked _like this:_
Ubuntu
Ubuntu (recovery mode)
Memtest 
Windows
How does it look now?

That's what I would to get back to!
OK here we go.

Ubuntu 7.10
Ubuntu 7.10  Recovery mode
Ubuntu 7.10  Memtest
Other Operating systems
MS Windows XP
Ubuntu 7.10......Generic  "This is the one that I use, gives a straight login, others give user/pswd"
Ubuntu 7.10  Recovery mode
Ubuntu 7.10 Memtest

Nothing is ever straight forward for me:confused:

---

### Post by aktiwers on 2008-01-05
Sorry this is also because I don't have that much experience with this.

But don't worry, we'll find out :)

Lets try remove that kernel then:
```
sudo apt-get remove linux-rt
```Let me know if that works..

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> Sorry this is also because I don't have that much experience with this.

But don't worry, we'll find out :)
Lets try remove that kernel then:
```
sudo apt-get remove linux-rt
```Let me know if that works..

Sorry didn't appear to do anything.see screen shot

---

### Post by aktiwers on 2008-01-05
Okay, atleast that showed us you have some libs that you dont need anymore. So you might as well run:
```
sudo apt-get autoremove
```
To clean that up :)

Anyways, back to topic..
Here is another idea:
When you have the menu.list open press CTRL+F and search for: howmany

You will see the lines:
> ##      howmany=7
# howmany=all

Now replace "all" with 4.

Then save and in Terminal type:
```

sudo update-grub
```

Did this help? 

Sorry, as stated I'm no Guru in this, but Im sure we will get this fixed. It should be simple.

---

### Post by newbeeman on 2008-01-05
> **aktiwers said:**
> Okay, atleast that showed us you have some libs that you dont need anymore. So you might as well run:
```
sudo apt-get autoremove
```
To clean that up :)

Anyways, back to topic..
Here is another idea:
When you have the menu.list open press CTRL+F and search for: howmany

You will see the lines:
Now replace "all" with 4.

Then save and in Terminal type:
```

sudo update-grub
```

Did this help? 
Sorry, as stated I'm no Guru in this, but Im sure we will get this fixed. It should be simple.

No go.
I used the autoremove and took some 70+MBs out.
Tried the terminal command, but CTRL+F didn't work.
Going to leave it for now, other matters more pressing. Will pick it up later.
Thanks for you help. Nearly there  :lolflag:

---

### Post by aktiwers on 2008-01-05
Okay mate.. sorry I couldnt be at more help.

Just one thing.. the CTRL+F should be pressed after you run the:
 ```
gksudo gedit /boot/grub/menu.lst
```

You know.. inside the text-editor :)

---

