---
title: "Updated and Windows is missing"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Kristy on 2006-09-15
Well ... I had things set up as dual boot with windows booting first. I decided that I wanted to install KDE.  So I did ... (sudo aptitude install kubuntu-desktop).  I dont think it went through the first time.  I rebooted and tried to change my session, but KDE wasnt listed.  So I installed KDE again.  Then I installed Easy Ubuntu (to make things easy) ...

I restarted session into KDE.  An icon in my "task bar" said there were updates.  So I installed updates.  I installed tuxmath and a few other apps.

Next I rebooted.  This time however ... There is 4 listings for ubuntu in GRUB and NO WINDOWS.  :confused: 

sudo gedit /boot/grub/menu.lst

[INDENT]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/hda3 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1[/INDENT]

 sudo fdisk -l
[INDENT]Disk /dev/hda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1297    10418121    7  HPFS/NTFS
/dev/hda2            2470        4963    20033055    f  W95 Ext'd (LBA)
/dev/hda3            1298        2469     9414090   83  Linux
/dev/hda5            2525        4403    15093036    b  W95 FAT32
/dev/hda6            4404        4963     4498168+   b  W95 FAT32
/dev/hda7            2470        2524      441724+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/INDENT]

Id really appreciate any help anyone could give me.  I cannot imagine this update overwriting XP.  Im fed up with XP, but I do need it for some things.  :-)

---

### Post by Najand on 2006-09-15
Add:
> title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

to the end of your /boot/grub/menu.lst
and try to reboot your computer.

---

### Post by bulldog on 2006-09-15
Put this at the end off your menu.lst

 title Windows 95/98/NT/2000
 root (hd0,0)
 makeactive
 chainloader +1

just under /dev/hda1 and it should work again.

You've got a kernel update that's why there are four entry's for Ubuntu.

---

### Post by akniss on 2006-09-15
Try adding the following entry into /boot/grub/menu.lst above or below the section marked 'AUTOMAGIC KERNEL LIST'.  Anything between those markers in the menu.lst file will get replaced periodically when the kernels are updated.  Placing the Windows entry before or after this region will keep it from being replaced.

```
title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by Kristy on 2006-09-15
ok. I will add this  ... and repost results.  Does everything else look ok.  Why do I have 4 different Ubuntu choices in Grub. How do I remove them ... I surely dont need 4 ..... do I?

---

### Post by Najand on 2006-09-15
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
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
timeout 10

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
# kopt=root=/dev/hda3 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
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

title Ubuntu, kernel 2.6.15-26-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot
[COLOR="Blue"]
title Ubuntu, kernel 2.6.15-23-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
boot[/COLOR]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


```

Commenting is a good way for not making serious problems; put a '#' sign before all lines in blue.

---

### Post by Najand on 2006-09-15
> **akniss said:**
> Try adding the following entry into /boot/grub/menu.lst above or below the section marked 'AUTOMAGIC KERNEL LIST'.  Anything between those markers in the menu.lst file will get replaced periodically when the kernels are updated.  Placing the Windows entry before or after this region will keep it from being replaced.

```
title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

Sorry bud... It is not [COLOR="Red"](hd0,1)[/COLOR], but in his  case it is [COLOR="Blue"](hd0,0)[/COLOR]

---

### Post by Kristy on 2006-09-15
Ok it worked.  I added it to the bottom.  now to make XP boot first, I move it to the top ... correct?  Why did updating add 2 more entries to GRUB.  Just comment them is all I need to do.  If  I move XP to the top, whaaat are the chances of it overwriting again?  

Once again, Thanks a million

---

### Post by Najand on 2006-09-15
When a new kernel installs, grub add two lines (sections) to the begining of your menu.lst So your first option would be third.

---

