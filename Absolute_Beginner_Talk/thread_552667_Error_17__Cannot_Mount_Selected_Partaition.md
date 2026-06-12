---
title: "Error 17 : Cannot Mount Selected Partaition"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by Jttm69 on 2007-09-16
Just so you know, i am hellaNoobzor. This is what i did so far;
I have windows xp sp2 installed on my 250 sata drive. i have a 80gb ata drive that is empty.(I also have a seccond 250 sats pluged in with nothing on it yet and a 160bg ata with media on it) So i wanted to try out Ubuntu and downloaded the CD install.  I burned it off, and put it in and restarted, booted it from the boot menu and i was at the install screen.  I booted it from the CD.  When i was installing from the cd, i chose the 80GB HDD.  It finished install without a problem.  At the end of the options though, i noticed that it had an option as to where i should install the bootlooder. I left it the way it was, and installed.  When i restarted it wouldn't load the bootlooder screen.  So i went into the bois and changed the boot order to the 80gb first.  I restarted and i got to the bootlooder screen and i chose Ubunto.  I get an Error: 17 Cannot Mount Selected Partaition.  I had to go back to my bois to get my windows xp drive to boot up agian.  Let me know what you think. 

 Guy

---

### Post by DezSP on 2007-09-16
We need to see your /boot/grub/menu.lst file. Boot with the live CD, mount your Ubuntu filesystem and paste that file here.

---

### Post by Jttm69 on 2007-09-16
where/how do i do that?

---

### Post by DezSP on 2007-09-16
Apologies. Let me be a bit more detailed. Once you've got Ubuntu running from the Live CD (as you did for installation), go to Places -> Computer and double-click the hard disk volume which corresponds to your new installation. It'll most likely say something like "xx.x GB Volume" and will have folders like bin/, boot/, lost+found/ in it (n.b. the one called "Filesystem" is NOT the one you want). Once you're in there, go to boot/grub/ and open up menu.lst, then paste the contents of that file here.

---

### Post by Jttm69 on 2007-09-16
menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by DezSP on 2007-09-17
Make a backup copy of menu.lst somewhere, then change the following:

Change:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```
To:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=[COLOR="Green"](hd0,0)[/COLOR]
```

And change:
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet
```

To:
```
title Ubuntu, kernel 2.6.20-15-generic
root [COLOR="Green"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root [COLOR="Green"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b3046ea5-6e8a-4176-be62-f8f478d310c7 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root [COLOR="Green"](hd0,0)[/COLOR]
kernel /boot/memtest86+.bin
quiet
```

Good luck!

---

### Post by Jttm69 on 2007-09-17
Ok, i understand all instructions thus far.  But i can unto a small problem.  The Menu.Lst file, is read only.  And when i start Ubuntu off the CD, it won't let me change the file.  It says i don't have permission to do that.  Also, will these changes stay changed? Even though it says when i boot the cd, that all changes will not be saved?

---

### Post by Jttm69 on 2007-09-17
Could not save the file /media/disk/boot/grub/Menu.lst.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by nb123 on 2007-09-17
Jttm69, okay, you installed it to your USB hard disk right? So remove your CD from the drive and boot your USB hard disk. Once you get to your grub bootloader screen, and when Ubuntu Kernel....  is highlighted, press 'e' to edit it, and then at the line 'root (hd1,0)', press 'e' again, now, change the hd1 to hd0, press 'enter', and then press 'b' now you'll be able to boot ubuntu. 

After this, to make this change permanent, open a terminal, and type this: ---

sudo gedit /boot/grub/menu.lst

it'll prompt you for your password, enter it, and then make the changes DezSP asked you to, be very careful not to change anything else. Save the file, and you're all set man

---

### Post by Jttm69 on 2007-09-17
Hey, that worked great.  I am installing the updates and such, and then i will restart to see if it really will keep working. hehe.   But, ive come to a standstill with the next step on installation.  I am confused (Because ive been using windows) Do i need to install my chipset drivers? Also, i know i have to install my Video driver, but i have no clue how.  Ive been looking at the other posts, and not sure if their problems relate to me.  I also have a external USB auido device, will ihave to install drivers for that as well??

---

### Post by nb123 on 2007-09-17
oh man, that's a lot of drivers :), I'm pretty new to linux too, I'm normally a windows user too, I don't know how much advice I can give you there, but I suggest get your internet up and running in ubuntu, and then checking to see what works and what doesn't, and typing 'lspci' in your terminal to get a list of your hardware devices, then perhaps checking them up in the forum if they're not working, someone's probably gotten them to work... have you got your internet up yet? If not, what kind of card / chipset you have?

---

### Post by DezSP on 2007-09-17
Most drivers will be included in the kernel, you shouldn't worry about them unless something's not working. The video driver will usually be found in System -> Administration -> Restricted Drivers Manager.

If you have nonfunctioning hardware, best thing is to Google the device name for a how-to guide.

---

### Post by Jttm69 on 2007-09-17
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

so i used that link, to activate my ati drivers.  I used only the first few lines, because when i went to System/Admin/Restricted driver manager  i clicked "enable" and it installed a few things, rebooted, and i assume the video is all set?  If it is, where do i go to configure.  Also, my other questions from the last post still remain.

 Guy

---

### Post by Jttm69 on 2007-09-17
ok, so i can start Ubuntu from the selected list no problem.  But under the "other operating systems" my Windows xp doesn't start correctly, says missing ntldr .  (If i remember correctly.)

---

