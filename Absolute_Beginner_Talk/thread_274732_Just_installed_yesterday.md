---
title: "Just installed yesterday"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by adrian604 on 2006-10-10
Alrighty then.  I just installed Ubuntu yesterday and I partitioned the disk into 2 primary partitions, 1 extended and 1 swap.  I previously had WIndows XP installed but I fear I pretty much deleted it.  I'm not sure because I can't seem to boot windows with GRUB and the partition that I made for windows, the NTFS is said to be completely unused and not even formatted.  Please help a noob out?

---

### Post by Iarwain ben-adar on 2006-10-10
Hi,
first of all, welcome!

Hope you find all of your questions answered here..

Now,
you say that you partitioned your HD into 2 partitions..
Could you post the output of this command?
```
sudo fdisk -l
```

(you insert this in the terminal)


Iarwain

---

### Post by jorn on 2006-10-10
If you would like to see if your xp is still existing you could boot up the xp install-cd get into recovery mode and type> fixmbr then reboot.
If you just want to install Ubuntu,the installer will do the partitioning for you.

---

### Post by adrian604 on 2006-10-10
yes i surely can. the responce is-


Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by Straevaras on 2006-10-10
> **jorn said:**
> If you would like to see if your xp is still existing you could boot up the xp install-cd get into recovery mode and type> fixmbr then reboot.
If you just want to install Ubuntu,the installer will do the partitioning for you.

Just a warning, if you successfully fix the master boot record and your Windows partition does still exist, you'll lose the capability to boot to Ubuntu.  You would have to use the NT Bootloader or reinstall Ubuntu at that point.

OR...on second thought, just reinstall GRUB.

[How to Restore GRUB from Live CD](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by Iarwain ben-adar on 2006-10-10
> **adrian604 said:**
> yes i surely can. the responce is-


Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

Hi,
it's ```
sudo fdisk -l
```

the -l is a L (but not uppercase)

;)


Iarwain

---

### Post by adrian604 on 2006-10-10
Ahh yes yes i see i see.  haha ok here it is.

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6032    48452008+   5  Extended
/dev/hda2            6033       16749    86084302+   b  W95 FAT32
/dev/hda3           16750       24154    59480662+   7  HPFS/NTFS
/dev/hda4           24155       24321     1341427+  82  Linux swap / Solaris
/dev/hda5               1         133     1068259+  83  Linux
/dev/hda6             134        2245    16964608+  83  Linux
/dev/hda7            2246        6024    30354786   83  Linux
/dev/hda8            6025        6032       64228+  83  Linux

---

### Post by jorn on 2006-10-10
You'r right,Straevaras, there is probably a better way to examine the partitions. A long time ago I "copied" the "Smart boot manager" from the install-cd to a floppy disk and it has been of great value for me in order to boot from different patitions.

---

### Post by jorn on 2006-10-10
It seems you still have your xp. And a lot of linux ones. The application gParted which is a graphical patitioner will give you the option to delete, add and repartioning your hardisk. Maybe you should take alook at it. It's also available as live-cd.

---

### Post by adrian604 on 2006-10-10
how can i boot to windows was gunna b my next question to go to if i have it.  sooo, how can i boot to widnows?  =)

---

### Post by Iarwain ben-adar on 2006-10-10
Well,
just add this in your /boot/grub/menu.lst
```
sudo nano /boot/grub/menu.lst
```

```
title          Windows NT/2000/XP (loader)
root           (hd0,2)
savedefault
makeactive
chainloader    +1
```

So your menu.lst looks like this =>

```
<snip>

[I]title           Ubuntu, memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
boot[/I]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title          Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title          Windows NT/2000/XP (loader)
root           (hd0,2)
savedefault
makeactive
chainloader    +1
```      

The part in italics is NOT important (the root (hd1,6) part anyways..)


Iarwain


Btw: you save in nano by typing Ctrl+X ;)

---

### Post by adrian604 on 2006-10-10
umm ok how  wud i go abuot putting in all that stuff.  seems real confusing right now haha.  i get the menu part, hear-  

  GNU nano 1.3.10          File: /boot/grub/menu.lst                  Modified

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
                               [ Read 129 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell



where from here?  or where do i add that stuff.?

---

### Post by bulldog on 2006-10-10
Open your menu.lst and add it to the end of it```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by adrian604 on 2006-10-10
okay that seemed to have worked.  1 other problem now.  i get error 18 when trying to boot. so how can i overcome this (i think u gotta remap the boot sequense or something close to that, maybe idk i'm guessing from what i've seen before.)  btw you guys r great and very helpful =)

---

### Post by Iarwain ben-adar on 2006-10-10
> **adrian604 said:**
> umm ok how  wud i go abuot putting in all that stuff.  seems real confusing right now haha.  i get the menu part, hear-  
<snip>

where from here?  or where do i add that stuff.?

Well,
maybe do what bulldog said you to :D

It's a graphical way of doing it..

Btw: you can go down by pressing the down-arrow (and up by pressing the up-arrow)
You see a blinking cursor, and that's where you'd type..

But as i said, follow bulldog's advice ;)


Iarwain

---

### Post by bulldog on 2006-10-10
> **adrian604 said:**
> okay that seemed to have worked.  1 other problem now.  i get error 18 when trying to boot. so how can i overcome this (i think u gotta remap the boot sequense or something close to that, maybe idk i'm guessing from what i've seen before.)  btw you guys r great and very helpful =)

Error 18 means:Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Maybe you can update your BIOS with a newer one.

---

### Post by Iarwain ben-adar on 2006-10-10
Well,
i thought that that was the reason why Windows wanted to be installed first..

So it's bootable without too much fiddling :?

Could be wrong though,
just my 2cents


Iarwain

---

### Post by adrian604 on 2006-10-10
well larwain ur 2 cents are really worth like a couple a thousand $ haha.  mmm i dont liek to fiddle if i dont have at least **a little bit** of insight on what im sposed to do.    should i just upgrade the BIOS or is there another way- like i saw sumwhere the mapping method but i'm not sure at all.   

o and bulldog ur a good help as well.

---

### Post by Iarwain ben-adar on 2006-10-10
lol :D

Well,
according to [this](http://www.gnu.org/software/grub/manual/html_node/map.html) site,
i'd try to add this to your menu.lst

```

title          Windows NT/2000/XP (loader)
root           (hd0,2)
savedefault
makeactive
chainloader    +1
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
```

Just so you know,
i DON'T KNOW FOR SURE that this is correct ;)

Just trying to help :D


Iarwain

---

### Post by adrian604 on 2006-10-10
i'll do anything once or thrice.

---

### Post by Iarwain ben-adar on 2006-10-10
No problem then :D

Let us know how it goes! ;)


Iarwain

---

### Post by adrian604 on 2006-10-10
okay uhh that didnt work, still get the error 18.  (with the mapping codes from that site)  ummmm.  okay so shud i just go with the BIOS upgrade and try or duz uhh any one think theres hope still in the mapping?

---

