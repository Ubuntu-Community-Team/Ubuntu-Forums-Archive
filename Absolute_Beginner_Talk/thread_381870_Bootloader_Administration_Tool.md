---
title: "Bootloader Administration Tool"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by hansyje on 2007-03-11
Hi guys,

I am a beginner with Ubuntu!

I was trying to change the order the systems instaled in my computer boot .. I looked for help and i received the following advice:

[I]Getting started

You can start Bootloader Administration Tool in the following ways:

Applications menu

Choose System Tools &#8594; Boot.
Command line
 Execute the following command: boot-admin
When you start Bootloader Administration Tool, you will be prompted for the administrator password, this is necessary because the changes done with this tool will affect the whole system.

After entering the administrator password, the following window is displayed.

The Bootloader Administration Tool main window contains the following elements

     This is a list of the current options in your bootloader menu, beside the list there are buttons for adding new options, and modifying or deleting the already created ones.x

    	   
"Starting your computer" section
  		

    This let's you specify the time that the bootloader menu will be displayed before running the default image.[/I]





The thing is that i do not have (or i do not find) the Bootloader Administratice Tool and it is not under System Tools!

Can anybody help me to  find this tool for changing the order the installed systems in my machine boot? 

I checked your help online trying to edit the commands, but it seems that i am not good with it, so this can be my chance to do what i want!

Thank you!

---

### Post by mikewhatever on 2007-03-11
I do not have that too in 6.10. To edit the boot loader menu:
> cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

The first command will back up the menu file, the second will open the menu file in a new window. To change the default application to boot, change the following section > # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		6 
6 is the number of my Windows Home which boots by default. Yours may be different, so count the Title entries.


To change the time to show the menu, edit the following section:
> ## timeout sec
# Set a timeout, in seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5
mine is set to 5 sec, but you can change it to a different non zero value. Placing # in the beginning of that line will make the time infinite.

If you can't figure it out, post the menu here.
If you want to study more, check this page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Najand on 2007-03-11
I am not very familiar with "Bootloader Administration Tool"; However how do you want to change the order of your boot menu?

---

### Post by Tomosaur on 2007-03-11
I've never seen this tool, either.

In any case, if you're trying to play around with grub, you need to take a look at the /boot/grub/menu.lst file.

Alternatively, check the link in my sig.

---

### Post by hansyje on 2007-03-11
> **mikewhatever said:**
> I do not have that too in 6.10. To edit the boot loader menu:


The first command will back up the menu file, the second will open the menu file in a new window. To change the default application to boot, change the following section  
6 is the number of my Windows Home which boots by default. Yours may be different, so count the Title entries.


To change the time to show the menu, edit the following section:

mine is set to 5 sec, but you can change it to a different non zero value. Placing # in the beginning of that line will make the time infinite.

If you can't figure it out, post the menu here.
If you want to study more, check this page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This what i tried before and it didn't work for me.. i was not sure what to change and what not..

This is the menu:

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
# kopt=root=UUID=84dd4556-e917-41b3-aa2e-2f797ea990b4 ro
# kopt_2_6=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Najand on 2007-03-11
What do you want to change... If you sppecify it, we can edit your menu.lst for you.

---

### Post by hansyje on 2007-03-11
Thanks for the help!

Default booting system WIndows XP

Timeout 3 sec

Could you please highlight what you are changing? I can use it for future references and this way i learn smth new!

---

### Post by Najand on 2007-03-11
Change these red parts to blue ones:
> 
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
[COLOR="Red"]default 0[/COLOR] >>>[COLOR="Blue"]default 6[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout 10[/COLOR]  >>> [COLOR="Blue"]timeout 3[/COLOR] 

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
# kopt=root=UUID=84dd4556-e917-41b3-aa2e-2f797ea990b4 ro
# kopt_2_6=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title Ubuntu, kernel 2.6.17-11-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda7 ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda7 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by mikewhatever on 2007-03-11
In the very beginning of the menu file, in the following section
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

change the 0 to 6

and in the following section,
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

change 10 to 3

---

### Post by hansyje on 2007-03-11
Thanks a lot!

It seems that it was in front of my eyes!

Hope this is useful for other people too!

---

