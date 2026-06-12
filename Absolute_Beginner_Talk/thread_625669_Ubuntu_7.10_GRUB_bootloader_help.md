---
title: "Ubuntu 7.10 GRUB bootloader help"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by suffer1989 on 2007-11-28
Hey, Im a long time windows user,(10 yaers) when i decided to try to use ubuntu. I'm liking hows it working out and all, but i use ubuntu as my "secondary" system as all my apps only work on XP. Anyway, how do you configure the bootloader to automatically startup windows and only give me the boot options when i hit a certain key ? If it helps, I have pasted my "menu.lst" below.....

:KS
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
# kopt=root=UUID=27e315a7-32e4-4f8d-9a36-2ace730bc6bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,9)

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
root		(hd1,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=27e315a7-32e4-4f8d-9a36-2ace730bc6bd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=27e315a7-32e4-4f8d-9a36-2ace730bc6bd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,9)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

:KS


Thanks for the help :D....

EDIT: LOL @ smileys on 1st line  :guitar:

---

### Post by fineas on 2007-11-28
Just check this: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

---

### Post by subs on 2007-11-28
why dont u change the default OS to be loaded as windows.... and decrese the time out before ubuntu is loaded

---

### Post by kdarkentity on 2007-11-28
I have done alot of edit and customizing the grubs menu.lst recently and from  my understanding of it  the grub boots up the first highlighted  selection. Soo would it be enough for you to have your windows boot option at the top of your grub list? 

If so open up a terminal and do this.

gksu gedit /boot/grub/menu.lst

Go to the bottom the the menu.lst and look for the line that says "This entry automatically added by the Debian installer for a non-linux os"

below that line should be the entry to boot into your windows partition, simply just cut and paste this entry right above your Ubuntu grub entry, save your changes and restart to see if it works.

---

### Post by mahiyar on 2007-11-28
In the second para the line here
>  ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[B] default        0
[/B]controls which system will boot first, count from the top without considering the hashed entries #, start counting from zero and count the word title. In your case it will be number 4. 

From the command line >>sudo gedit /boot/grub/menu.lst (lst starts with small L), then in the editor change the default from 0 to 4. Next time windows will start. If you want you can reduce the 
timeout here
>  ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
** timeout        10**from 10 to something like 4 or 3. Do not set it to zero, if something goes wrong you will never be able to boot Ubuntu. If you want to boot Ubuntu press any arrow key to stop the timer.

I still would suggest to make Ubuntu the primary one.

---

### Post by Tomosaur on 2007-11-28
Change the line which says:
```

default 0

```

so that it says
```

default 4

```

You have FIVE items in your Boot menu, INCLUDING the separator line which says 'Other Operating Systems', but Grub counts from 0, so the fifth and final option in your boot menu is counted as '4'.

To hide the menu, change the line which says:
```

#hiddenmenu

```

so that it says:
```

hiddenmenu

```

(In other words, just remove the '#' from the beginning of the line. Your menu should now be hidden, and will only show up when you press Esc.

You can also shorten the delay between Grub loading and your OS booting by altering the 'timeout 10' line to something shorter, say 'timeout 3'. This will give you a 3 second delay before Grub boots into Windows.

Please do not use the Grub Editor in the link in my sig since you're using Ubuntu 7.10 - there is a bug which I'm trying to fix which will almost certainly mess your boot menu up. For now you will just have to change your defaults manually.

To edit the file, hit alt+f2, then type 'gksudo gedit /boot/grub/menu.lst'. Type in your password in the box which appears, and the file should load in gedit. Then, find the 'default 0' line and change it to 'default 4'. Make any other changes you wish to make, too. Save the file, then exit, and next time you boot up, it should boot into Windows automatically.

---

### Post by Dedoimedo on 2007-11-28
Hello,
Just change the default from 0 to relevant other entry. Entries are counted from 0 up.
Windows is your 5th entry, therefore change to default 4.
Regards,
Dedoimedo

P.S. Just noticed a great post above mine ...

---

### Post by suffer1989 on 2007-11-28
Thanks for the help guys, all is in order. (i'm typing this from ubuntu)

---

