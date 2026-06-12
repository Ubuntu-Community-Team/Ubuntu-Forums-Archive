---
title: "grub continues to hate me"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by fallenfantasyx on 2007-09-16
i recently installed ubuntu 7.04 on my second hard drive...this is my setup

1st sata drive 
10gb parition for windows
230gb partition for storage (NTFS)

2nd sata drive
20gb for /
310gb for /home
2gb for swap

3rd hard drive (ide)
120gb for storage (ntfs)

i boot from the live cd and go through install and keep getting grub 22 errors, and having to go back and use windows fixmbr...

ive tried super grub disk, and live cd grub install and i always get the error 22, i even switched the order of my sata drives to see if that helps, it boots grub menu but everytime i hit enter for the entries it says partition not found

i wish ubuntu had a more advanced options for installing grub all the advanced tells me is its going to be installed on (hd0) which is what i want in the MBR...

any help would be awesome...ive gone through all the tutorials on these forums related to grub and still no luck, i wouldnt mind using the ntldr i just want my linux to work >.<

---

### Post by SpiritIsReality on 2007-09-16
howdy
first off, I don't know if this is going to be of any help,
if it isn't, you should probably post again so that your
post shows 0 replies. 

in this thread it talks about setting your bios to boot off the
second sata.
[http://ubuntuforums.org/showthread.php?p=2228249](http://ubuntuforums.org/showthread.php?p=2228249)
from here
[http://www.google.ca/search?hl=en&q=+ubuntu+grub+%2B2+sata+-pata+-ide+-raid&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=+ubuntu+grub+%2B2+sata+-pata+-ide+-raid&btnG=Search&meta=)

[http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+grub+sata&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+grub+sata&btnG=Search&meta=)
on these pages, click on edit (top left of window),find in this page, at bottom of page type in sata, click on
next...next... It mentions that you might have to tell grub to install to sd0.

worth looking here
[http://ubuntuforums.org/showthread.php?t=473962](http://ubuntuforums.org/showthread.php?t=473962)
from here
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+grub+%2B2+sata+-pata+-raid+-ide&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+grub+%2B2+sata+-pata+-raid+-ide&btnG=Search&meta=)

[http://www.linuxforums.org/forum/ubuntu-help/85672-another-grub-mbr-headache.html](http://www.linuxforums.org/forum/ubuntu-help/85672-another-grub-mbr-headache.html)
from here
[http://www.google.ca/search?hl=en&q=grub+%2B2+sata+-pata+-ide+%2B%28ubuntu+%7C+debian%29+-raid+mbr+code+%2B22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=grub+%2B2+sata+-pata+-ide+%2B%28ubuntu+%7C+debian%29+-raid+mbr+code+%2B22&btnG=Search&meta=)

[http://linuxgazette.net/141/anonymous.html](http://linuxgazette.net/141/anonymous.html)

Sef ...thankyou
and all ...thankyou

trails

---

### Post by Sef on 2007-09-16
> (GRUB) 22 (error) : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2) Did you burn the iso at 4x or less?

3) Did you check the cd for defects?

---

### Post by fallenfantasyx on 2007-09-16
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=82be7e85-be92-40a0-bd82-08a5920f3ebd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=82be7e85-be92-40a0-bd82-08a5920f3ebd ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
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


thats what my menu.lst says if it helps

---

### Post by fallenfantasyx on 2007-09-16
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=82be7e85-be92-40a0-bd82-08a5920f3ebd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=33146ba1-696f-488e-b063-67b0362fc19e /home           ext3    defaults        0       2
# /dev/sda1
UUID=0CA03288A03277F2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=DC3881183880F336 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc1
UUID=B65089355088FCFD /media/sdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=fd0342b4-3f4f-44e6-86bc-8673b824792c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by mikewhatever on 2007-09-16
Hi fallenfantasyx,

Unfortunately, the more HDDs you have, the harder it gets for grub to figure out how to set up itself. It is usually fixable though.
You'd have to boot with the live CD and mount your Ubuntu root partition. The way it is done is shown here [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
Note, your partitions' names may differ, so check what they are first.
Once the partition is mounted, we are interested in several files: /boot/grub/menu.lst, /boot/grub/device.map.
Save them to some external storage and post here.

Oh, you've done it already. It looks like this part > title Ubuntu, kernel 2.6.20-15-generic
[COLOR="DarkOrange"]root (hd1,1)[/COLOR]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=82be7e85-be92-40a0-bd82-08a5920f3ebd ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

should look like this
> title Ubuntu, kernel 2.6.20-15-generic
[COLOR="DarkOrange"]root (hd1,0)[/COLOR]
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=82be7e85-be92-40a0-bd82-08a5920f3ebd ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

You can edit the boot line by hitting ESC when seeing the timer counting, highlighting the boot line and hitting e. If it works, edit the menu.lst to make the changes permanent.

---

### Post by DezSP on 2007-09-16
Grub does have a command-line interface, if you're feeling a bit bold. Load up the grub menu, press c, and you can use the geometry command to find out what's going on; e.g. geometry (hd0)

It'll list out the partitions as grub sees them at boot-time. You can then use this info to edit the root line as Mike suggested to the correct values.

Be aware though that if you alter the values directly in menu.lst, Ubuntu may well overwrite them at some stage. There are some Debian config options in there before the kernel list which should allow the file to be generated properly. Good luck!

---

### Post by fallenfantasyx on 2007-09-16
Can i just edit that line from hd 1,1 to hd 1,0 in windows with text editori do have access to the files in windows thx to EXTifs2 :D

---

### Post by mikewhatever on 2007-09-16
Yes you probably can.

---

### Post by SpiritIsReality on 2007-09-17
howdy

active grub thread here
[http://ubuntuforums.org/showthread.php?t=552832](http://ubuntuforums.org/showthread.php?t=552832)
probably worth looking at
sorry I'm not a grub geek yet, but it seems you're meant to be in short order.
hopefully you're in the saddle and runnin' linux toute suite.
at aboutdebian.com they suggest getting a reasonable comp to practice
with, may pay off, I got two handmedown pII's, and they're not too bad 
compared to this pIII powerhouse I'm using now.
lookin' forward to an amd64

via con dios

trails

if'n I was you, I'd keep at this forum till you get somebody to wrangle you
a ride with linux. There's plenty of high class wranglers around here for sure.

---

### Post by nonewmsgs on 2007-09-17
> **DezSP said:**
> 

Be aware though that if you alter the values directly in menu.lst, Ubuntu may well overwrite them at some stage. 

i have seen that thing happen before and i thought i was going nuts...

---

### Post by nonewmsgs on 2007-09-17
also check this out
[http://ubuntuforums.org/showthread.php?t=543680](http://ubuntuforums.org/showthread.php?t=543680)

---

