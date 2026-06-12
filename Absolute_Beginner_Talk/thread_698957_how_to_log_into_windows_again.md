---
title: "how to log into windows again"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by cherankrish on 2008-02-16
hi,
my laptop is acer aspire with windows vista home pre.ive put ubuntu on d drive.
now i couldnt go to vista os. it should have to ask me to select opperating system but didnt.directly goes to ubuntu.after that i just want to reformat every thing and put windos xp again. but when i boot using windows xp setup it says' no hard disk found'.

what is the solutions for this? if i see windows vista still existing on my c drive.
i need to use the vista again or put windows xp with ubuntu
can any one help please?

regards
cheran

---

### Post by JoshuaRL on 2008-02-16
Could you post the output of:

```

gksu gedit /grub/menu.lst

```

---

### Post by cherankrish on 2008-02-16
im new to linux. where can i type this code?

---

### Post by kryth on 2008-02-16
Applications>>accessories>>terminal

you can copy and paste

---

### Post by JoshuaRL on 2008-02-16
That's fine.  We were all new once :)

Go into Applications->Accessories->Terminal.

EDIT
Aw, beat me to it!
/EDIT

---

### Post by kryth on 2008-02-16
It will pop open another window that's a text editor named 'gedit'.   Just copy and paste the whole thing here.

---

### Post by kryth on 2008-02-16
Tag! You're it.

---

### Post by cherankrish on 2008-02-16
i recevied 


While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by cherankrish on 2008-02-16
a text editor opened.but it was blank

---

### Post by kryth on 2008-02-16
gksu gedit /boot/grub/menu.lst


try that, that should be right......the 'boot' part was missing

---

### Post by cherankrish on 2008-02-16
you master.worked.this is the results

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
# kopt=root=/dev/sda3 ro

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by JoshuaRL on 2008-02-16
Thank you very much!  What I was looking for in there was if you had wiped the drive or left Windows on it.  Go ahead and close that, you won't need to edit anything in there yet.  

Next time you boot and it says Loading Grub, hit Esc.  That will load up a menu that will allow you to choose what OS to load.  See if Vista boots when you choose it and hit enter.

---

### Post by kryth on 2008-02-16
EDIT DON"T DO YET. JOShuaRL probably knows better than me.


okay 
do this 
gksu gedit /boot/grub/menu.lst

Add everything below this to the very end of the opened file. Save. Reboot and you should have a choice between vista and ubuntu. I hope :)




# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by cherankrish on 2008-02-16
can anyone say , why i recevied the 'no hard disk installed ' error message when i trying to install windows again?
or how can i reinstall windows xp?

ill post agin after i restart and see the results .thankx kryth and Joshua

---

### Post by MasterJS on 2008-02-16
The problem might be the MBR. By having GRUB installed to it, it might have messed it up. You'll need to repair it.

---

### Post by cherankrish on 2008-02-16
when i press escape button.i got
windows vista boot manu. after i hit it started to load windows vista.but windows start failed with ' couldnt find language ui images' on c:windows/imag(im not shure about this path) .then authomatic restore started.that also failed with this 'restore failed reson 0 x 90000001'

---

### Post by MasterJS on 2008-02-16
I think you need to repair your windows partition

---

### Post by cherankrish on 2008-02-16
Masterjs , i couldnt understand.im new to this area. see 'Absolute Beginner Talk' :)

---

### Post by JoshuaRL on 2008-02-16
Yep it's MBR.  From the Windows Installer CD go into the Recovery Console and put in:

```

FIXMBR
FIXBOOT

```

I think.  I don't have a ton of Windows CLI experience.  But I think that should allow you to reinstall Windows.  Then you should try reinstalling Ubuntu from the LiveCD.  Pick the Guided Partition method.  Then just use the slider to pick the size of the Ubuntu partition.

You see, Windows rewrites the entire MBR (Master Boot Record).  So when you tell it to FIXMBR, then it will write over Grub, allowing you to run ONLY Windows.  You would either use SuperGrub to reinstall Grub, or just reinstall Ubuntu.  That will be the easier one, but you will loose all your data on the drive.

---

### Post by cherankrish on 2008-02-16
joshu ..ill try and give u a pm

---

### Post by cherankrish on 2008-02-16
KRYTH, Joshua ,MasterJs thank you friends .
it has been fixed by the code which kryth gave earlier.

Joshua ive to thank you. you replied me wt in one minute after ive posted.
you friends have been wt me more than 40 minuts.Thankz for your time.
continue to help .Thank you and Thank you

---

### Post by JoshuaRL on 2008-02-16
Cool.  You might want to go up to the top at Thread Tools and Mark As Solved.  Also, you can thank those that helped you with the little gold star over on the bottom right.

[RIGHT]\/ . . . Over there.[/RIGHT]

---

