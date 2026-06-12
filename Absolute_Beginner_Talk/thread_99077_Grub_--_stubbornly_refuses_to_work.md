---
title: "Grub -- stubbornly refuses to work"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by j.hill on 2005-12-04
OK, I've been on Ubuntu since July or thereabouts, so I'm not sure I qualify as an absolute beginner.  I don't fear the terminal.  But I'm still definitely a n00b, which is relevant because I have a problem that everyone in the more advanced forums seems able to solve.  That said:

I had a dual-boot setup with Ubuntu on the master drive, W2K on a slave drive, and Grub providing the menu.  At first it worked perfectly.  Some months ago I totally hosed my installation (I'm still not sure how), and had to re-install Ubuntu.  Once that was done, Grub would only let me boot into Ubuntu.  W2k is still on the boot menu, but I get Grub's Error 11 (unrecognized device string) when I select it.

I have tried several of the remedies available on other Grub-related threads.  I have re-installed grub, grub-installed, chrooted, and so on.  I have consulted Grub's online documentation (opaque, yet uninformative).  I have booted from a live CD, opened a root terminal, offered incense to Richard Stallman, you name it.  The remedies other people swear by have not worked for me, and I'm getting incredibly frustrated.

Sorry to go on.  The point is:  how can I fix this problem?  For that matter, how can I *identify* the problem?  For all I know, none of those remedies are even relevant to the problem I need to fix.  

I can post the relevant part of /boot/grub/menu.lst if you want, but I'm pretty sure it's right.

I hate Windows as much as the next guy, but I need to use it occasionally.  

Thanks in advance.

---

### Post by SilentCacophony on 2005-12-04
Well, by the symtoms you describe, I would ask you to post the entire contents of these files:

/boot/grub/menu.lst
/boot/grub/device.map

and the output of this command:

sudo fdisk -l

making sure to wrap CODE tags around the menu.lst, at least.

Unfortunately, I won't be back soon to look at them, but someone might spot a problem in the meantime.

---

### Post by j.hill on 2005-12-05
As you requested:

**/boot/grub/menu.lst**

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows 2000 Professional
map		(hd1)(hd0)
map		(hd0)(hd1)
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
```

**/boot/grub/device.map**

```
(hd0)	/dev/hda
(hd1)	/dev/hdb

```

**sudo fdisk -l**

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2             852       14593   110382615    5  Extended
/dev/hda5             852        1122     2176776   82  Linux swap / Solaris
/dev/hda6            1123       14593   108205776   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9728    78140128+   7  HPFS/NTFS
```

Thanks again.

---

### Post by SilentCacophony on 2005-12-05
Hi. I do *believe* I've spotted the problem. The **Error 11 (unrecognized device string)** is one I'd not seen before, so I looked it up in the grub [manual]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html"). It says this:

> This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem.

Which made me look more closely at your Win2k entry, and I see that there appear to be no spaces between the device strings in the map commands, causing grub to think that they are only one device string each (in an invalid format.) Also I'm not sure if the order of the map commands matter, but I'll suggest the order that I usually see on working entries.

So, I'd try replacing your original entry shown here:

```
title		Microsoft Windows 2000 Professional
map		(hd1)(hd0)
map		(hd0)(hd1)
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
```

to this entry:

```
title Microsoft Windows 2000 Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

Note the spacing difference, and be careful of any further formatting. ;) Hopefully that fixes it.

If you have any further trouble after that (hopefully not!), I've often seen people suggest and entry like so, though it looks odd:

```
title Win2k
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1
```

Hope this helps.

---

### Post by j.hill on 2005-12-05
You, my friend, just racked up some serious karma.  I have a functioning dual boot for the first time in about four months!  You've got sharp eyes:  I've shown my menu.lst to some other people and no one spotted the spacing problem.  Heck, I didn't spot it myself -- not that I knew to look for it.  I had looked up that error in the Grub manual before, but I couldn't figure out what they were talking about.  The syntax looked perfectly fine to me.

Anyway, many many thanks.  I'll sleep easier with this frustration assuaged.  And once again I'm using Linux because I *want* to, not because I *have* to.

---

