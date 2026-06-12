---
title: "Can't Get Access To Vista"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by M4v3r1kk on 2008-03-02
So I've installed Ubuntu on an external hard drive, which had nothing on it before I did the installation, and it runs fine and dandy. Problem is when ever I try to launch Vista from GRUB, well, it just won't. I'll see 2 lines, of text, on a black screen and it goes back to the selection menu. Any help?

edit: Here is what the lines say

> 
Starting...
GRUB Loading Stage 2...


---

### Post by M4v3r1kk on 2008-03-02
Someone out there? Please? This is a very serious problem as I have need of files on my Vista drives, that I can't access, in two days :( .

---

### Post by NightwishFan on 2008-03-02
When I saw the thread title I was going to offer my congratulations but...

Jokes aside, perhaps try the search function for grub issues or one of the stickies may assist.

Edit: As a short term fix, you can mount your Windows partition in Ubuntu and get the files from there.

---

### Post by roachk71 on 2008-03-02
If you don't need to access Vista itself but really need files from that partition (and are connected to the Internet), try installing the **ntfs-3g** package through Synaptic. Then, you'll find the NTFS configuration tool under Applications-->System Tools. This tool enables writing to NTFS partitions, but be careful.

Beyond that, I really wish I could help you. I dumped Vista completely for Ubuntu after basically the same thing happened to me... :(

---

### Post by justsomedude on 2008-03-02
Please post

```
gedit /boot/grub/menu.lst
```

---

### Post by M4v3r1kk on 2008-03-02
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		5

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
# kopt=root=UUID=0ee4ce2b-eaad-4105-9d7a-df1628d653c7 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0ee4ce2b-eaad-4105-9d7a-df1628d653c7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0ee4ce2b-eaad-4105-9d7a-df1628d653c7 ro single
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
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1


There it is. I changed the 0 value to a 5 to try to see if it'll boot into Vista. Hope it does.

---

### Post by M4v3r1kk on 2008-03-02
Well the value didn't do anything. :(

---

### Post by justsomedude on 2008-03-02
> **M4v3r1kk said:**
> There it is. I changed the 0 value to a 5 to try to see if it'll boot into Vista. Hope it does.

What value?

menu.lst looks fine so far, now we need:


```
sudo fdisk -l
```

---

### Post by Maxcore on 2008-03-02
When you shut down vista make sure your shut it down correctly and ubuntu mounted it automatically for me

---

### Post by M4v3r1kk on 2008-03-02
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84c271ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  27  Unknown
/dev/sda2   *         893       10197    74742412+   6  FAT16
/dev/sda3           10198       19457    74380950    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000862ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        4864    19535040    5  Extended
/dev/sdb3            4865        4988      996030   82  Linux swap / Solaris
/dev/sdb5            2433        4864    19535008+  83  Linux

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              13       99200      991875+   6  FAT16
alexander@alexander-laptop:~$ 


The values I changed where for default launch on timeout. I changed it from 0 (Ubuntu) to 5 (Vista) but it didn't change a thing.

> 
When you shut down vista make sure your shut it down correctly and ubuntu mounted it automatically for me


I'll do that if and when I get access to Vista. /emo

---

### Post by M4v3r1kk on 2008-03-02
Well I'll wait a bit more for any replies but I found out I can rewrite my external HDD with my Live CD. Is this recommended? Considering everything to do with Ubuntu is on the external HDD would overwriting it bring things back to normal?

---

### Post by justsomedude on 2008-03-02
Okay, first attempt. Backup your menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then, change

```
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
chainloader +1
```

to 

```
title Windows Vista/Longhorn (loader)
root (hd0,2)
savedefault
chainloader +1
```


And another question: Does XP/Win 2000 (whatever it is) boot?

---

### Post by M4v3r1kk on 2008-03-02
The XP/ Win 2000/NT is Acer's way of recovering Vista.

I cannot save the changes I do in menu as it says I don't have permission.

---

### Post by justsomedude on 2008-03-02
open it like this:

```
sudo gedit /boot/grub/menu.lst
```

be sure to back it up first, as instructed above.

---

### Post by M4v3r1kk on 2008-03-02
This is what I'm getting now when I try to start Vista,

> 
Starting up...

MLDR is missing...
Press Ctrl + Alt + Del to restart...


Something interesting I found earlier but didn't think about. I can see my D: Drive but I can't see my C: Drive. Could this mean C: Drive is corrupted? I don't think it could be as Ubuntu was installed in such a way that it had no contact with Vista.

note: Sorry for the later reply, I fel asleep.

---

### Post by timbounceback on 2008-03-02
perhaps you mean NTLDR? found this on google: [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

### Post by DizzyTech on 2008-03-02
Perhaps you need to increment root (hd0,2) to root (hd0,3) for Vista's loader.  I know for a fact that Vista does not use NTLDR and, according to one of your previous posts, the only Windows XP-style thing you have on your copmuter is Acer's recovery partition, so it looks like you're trying to boot into that.

One thing you should do when you get into Vista (and you will) is burn Acer's recovery CDs/DVDs, so you can get rid of your recovery partition entirely.

---

### Post by tle89 on 2008-03-02
i'm getting,

starting up...

bootmngr is missing...
press ctrl+alt+delete to restart...

anyone know what to do?

---

### Post by M4v3r1kk on 2008-03-02
Well, time reveals one's stupidity.

I remembered that during installation I accidentaly whiped the C: Drive in partitioner but then clicked "Undo Partitions". The size was unkown before and after I partioned it and undid the partition.

My guess is that I have completely whiped C: Drive and may have start up recovery.

Any last comments before I do this?

---

### Post by M4v3r1kk on 2008-03-02
Well I just tried to switch from 2 to 3 and when I did restart and try to access Vista I got this,

> 
No such partition exists...
Well, time reveals one's stupidity.

I remembered that during installation I accidentaly whiped the C: Drive in partitioner but then clicked "Undo Partitions". The size was unkown before and after I partioned it and undid the partition.

My guess is that I have completely whiped C: Drive and may have start up recovery.

Any last comments before I do this?s

:( I guess I'll go into recovery soon. Faster I do it faster I can redo that one document so it is ready for tomorrow. Thanks for the help.

---

### Post by Happy_Man on 2008-03-02
> **tle89 said:**
> i'm getting,

starting up...

bootmngr is missing...
press ctrl+alt+delete to restart...

anyone know what to do?

It seems that in some way, when you installed Ubuntu to the external HDD, you replaced the Vista loader (which is different from the NTLDR that Grub is designed to be able to circumvent) with GRUB. This normally would not be a problem...if we were dealing with XP. With Vista, however, it's a whole different ballgame. I suppose the easiest way to fix this would be to pop in a Vista recovery disk and fix the bootloader. This can be accomplished by entering the command ```
fixmbr
``` at the repair console prompt. Now you will have Vista and XP back, but not Ubuntu. So, hop on over to the Super GRUB Disc site ([http://www.supergrub.forjamari.linex.org](http://www.supergrub.forjamari.linex.org)) and download and burn that. Use the directions found on this site ([http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)) to install GRUB *on the external hard drive*. Once you have finished all of this, you should be able to boot all your OSs. Just remember, if you want to boot Ubuntu, set your boot menu in BIOS to boot from the external HDD. 

Hope this helps!

---

### Post by tle89 on 2008-03-02
sorry i should've mentioned that it was on a partioned HDD with vista can i still do the same???

---

### Post by Happy_Man on 2008-03-02
Well, if your Ubuntu is on a partition instead of a separate HDD it's still doable, you just have to get GRUB onto the Ubuntu partition. Do the first bit about fixing your Vista bootloader, and then when it gets time to install GRUB again, merely install GRUB to the partition you have Ubuntu on, instead of another HDD.

---

### Post by tle89 on 2008-03-02
where do i enter the code fixmbr?

---

### Post by Happy_Man on 2008-03-02
You'll have to get a Vista recovery or Vista full install CD (no upgrade CDs) and boot from it. Follow the directions to get into a recovery console, and there you enter fixmbr.

---

### Post by tle89 on 2008-03-02
ok so i dont think my CD i have is a recorvery CD any other ideas?

---

### Post by M4v3r1kk on 2008-03-02
If you are using an Acer system you can access the recovery management by pressing Alt + F10 during the Acer boot up screen. From there you can select to default to factory settings or use a CD. I had my CDs with me so I didn't have to use the factory settings.

note: This is to fully restore Vista to the beginning which I ended up having to do (considering I did delete C Drive).

---

### Post by Aurora@FleetBuzz on 2008-03-02
Question on Post #6.

If the threadstarter had set the "default" to 4 instead of 5, would have he been able to boot into vista?

Is not the way to set the default OS the number derived from counting titles down from  0?  I only see 5 titles with Vista as #5.

---

