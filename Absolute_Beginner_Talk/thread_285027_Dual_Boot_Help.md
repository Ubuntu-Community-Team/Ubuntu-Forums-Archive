---
title: "Dual Boot Help"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by rwclardy on 2006-10-26
I have installed Dapper Drake on a windows xp system.  I used to gpart to partition the hard drive and it came us with sda3 for linux and sda5 for the swap.  The linux is running fine.

When I try to start windows xp, I get "filesystem type unknown, partition type 0x7."

I have been nosing around the grub from other postings here, but everything looks okay.  But then again, what do I know.

Any ideas?

Rob

---

### Post by bulldog on 2006-10-26
Can you give the outcome of ```
sudo fdisk -l
```

So we can see where your XP partition is.

Maybe you can give us your menu.lst too?
```
gedit /boot.grub/menu.lst
```

---

### Post by rwclardy on 2006-10-26
gedit output:
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

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
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
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

fdisk output
Okay, I am a moron.  I type the fdisk into the terminal and get a bad command message back.

---

### Post by bulldog on 2006-10-26
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

fdisk output
Okay, I am a moron.  I type the fdisk into the terminal and get a bad command message back.

Try copy & paste :D  is much quicker

---

### Post by Bartender on 2006-10-26
Did you type in an "ell" at the end or a "one"?  It's the letter 'l', not the number.
EDIT:  Sorry, I mean for the part of that command: 'fdisk-l'

---

### Post by rwclardy on 2006-10-26
yes.  I get bash: sudu: command not found

---

### Post by Coelocanth on 2006-10-26
> **rwclardy said:**
> yes.  I get bash: sudu: command not found

sud**o**, not sudu. ;)

---

### Post by Bartender on 2006-10-26
Try 'sudo' ;) It gets better with some practice

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> yes.  I get bash: sudu: command not found

It's sudo and not sudu```
sudo fdisk -l
``` l as in like

---

### Post by rwclardy on 2006-10-26
Okay, I typed in fdisk -L (in lowercase, but ending the confusion) and it comes back with nothing; just another command line.

I did take my medication thought, so things should look up in a few minutes.

---

### Post by rwclardy on 2006-10-26
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sda2           35377       36481     8875440    c  W95 FAT32 (LBA)
/dev/sda3           19582       34733   121708440   83  Linux
/dev/sda4           34734       35376     5164897+   5  Extended
/dev/sda5           34734       35376     5164866   82  Linux swap / Solaris

See it's working already

---

### Post by rwclardy on 2006-10-26
That would be the medication is starting to work, not the computer :-)

---

### Post by bulldog on 2006-10-26
As I see it your windows mediacenter is working correct??

Did you install XP on a fat32 partition?

How did you choose before Ubuntu was installed between the media center and XP?

I'm not familiar with mediacenter,that's why I'm asking.

Your menu.lst seems okay,but I think you have to start XP via media center if that was the case before you installed Ubuntu.

---

### Post by rwclardy on 2006-10-26
No, I had media center installed then installed daper.  The xp is on the ntfs partition.  The fat32 windows partition is the HP recovery portion of the disk.

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> No, I had media center installed then installed daper.  The xp is on the ntfs partition.  The fat32 windows partition is the HP recovery portion of the disk.

Well I see one NTFS partition.
This should be your media center.
Is XP on this partition too?

The partition grub expect's xp is your recovery partition.
Will not work as you know by now.

---

### Post by rwclardy on 2006-10-26
If you click the second windows options from the boot menu, it goes to a system recovery module where it wants to rewrite everything, which isn't the end of the world, but I really don't want to start over if I don't have to.  I just want access to the media center portion.

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> If you click the second windows options from the boot menu, it goes to a system recovery module where it wants to rewrite everything, which isn't the end of the world, but I really don't want to start over if I don't have to.  I just want access to the media center portion.

Yes I can agree with that.

But it's not clear to me.
You ask for XP,where is XP installed?

I have not much knowledge about mediacenter.
Explain to me what it is,an add on to your XP install,or a OS on it's own.

As I can see you have one NTFS partition.
Is XP and mediacenter on the same partition installed?

Could you start media center separate from XP before you installed Ubuntu?

---

### Post by rwclardy on 2006-10-26
Media Center is just another version of XP, think XP Home edition version 2.0.  They are one OS.  Does that make sense?

BTW, Thanks for you help and time so far.

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> Media Center is just another version of XP, think XP Home edition version 2.0.  They are one OS.  Does that make sense?

BTW, Thanks for you help and time so far.

Then should the first entry in your menu.lst [media center] pointing at sda1 will do as far as I can see.
The second entry pointing to sda2 should be removed.[later]

Try it an report what is happening please.

Before altering anything let's make a copy of your menu.lst :D ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```
Just copy and paste in your terminal.

---

### Post by rwclardy on 2006-10-26
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

How do you want me to change this?

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

How do you want me to change this?

This entry should do it for you without altering.

The second entry which points to XP on your sda2 [recovery] is the one you should remove from your menu.lst.

I understand XP and Media center is one and the same OS and is on your sda1 partition,which is correct pointed out in menu.lst.

You get the error in your first post from the media center entry?

Can't see anything wrong with your menu.lst exept the second windows entry.

Open your menu.lst ```
sudo gedit /boot/grub/menu.lst
```

Then ## = comment out the second windows xp lines,all of them.
Just put a # before each line.

I presume you have made your copy of menu.lst as suggested in my previous post?
If not make a copy first before altering.

**EDIT:**
If you made the changes then update grub```
sudo update-grub
```

Then try to boot Media center again.

---

### Post by rwclardy on 2006-10-26
I commented out the second XP entry.

The error I get when I select the XP home edition os is - "filesystem type unknown, partition type 0x7"

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> I commented out the second XP entry.

The error I get when I select the XP home edition os is - "filesystem type unknown, partition type 0x7"

See my edit in previous post.

You have to imagine GRUB expects a NTFS filesystem and does get something else to chew on.
That should indicate your menu.lst points to the wrong partition.

But it points to (hd0,0) which is the same as sda1,GRUB starts counting with a zero to make things simple.:D 

So your menu.lst should be okay as far as I can see.
But what confuses me is the second entry which is made by grub.
It indicates this entry is bootable so it is added to grub.

If this recovery partition was in your MBR it is possible your original XP-home was fired up by this recovery entry.

If so we have a little problem to solve.](*,)

---

### Post by rwclardy on 2006-10-26
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows NT/2000/XP
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1

Rebooted..  Same thing.

---

### Post by bulldog on 2006-10-26
> **rwclardy said:**
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows NT/2000/XP
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1

Rebooted..  Same thing.

Read my previous post and let me know what you know.

Do you have XP on a cd?
How valuable is your recovery partition to you?

The only thing I can think about is that the bootloader for your XP/Media center is not present.
You can boot the recovery partition however,what seems a little strange to me,but I never had a recovery partition,so it could be perfectly normal.

It seems to me this is a strange configuration.
Recovery will boot and the original will not.

I should imagine your recovery was activated by a floppy or a cd-rom instead of being bootable.

---

