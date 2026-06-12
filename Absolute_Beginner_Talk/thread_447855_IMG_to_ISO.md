---
title: "IMG to ISO"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-05-18
I've just found that IMG disc images don't mount on linux, so is there a program to convert .img images to .iso images on ubuntu?

---

### Post by lazyart on 2007-05-18
img2iso... though it looks like you'll have to build it.

---

### Post by starcraft.man on 2007-05-18
> **lazyart said:**
> img2iso

Really what repos are that in? I just did a search of all mine (I have all the extra repos I know of) and I only got these 3:
ccd2iso
mdf2iso
nrg2iso

I'd like to know myself where that is for future reference... I did a quick search myself of .img extension on the forums and most of them seemed to say ya just rename the extension .iso and burn with k3b >.>.

Edit: heh, edited your post, wheres the site with the source then?

---

### Post by lazyart on 2007-05-18
It's not in the repositories... that's why you'd have to build it yourself.

[http://www.t2-project.org/packages/img2iso.html](http://www.t2-project.org/packages/img2iso.html)

---

### Post by The Seeker on 2007-05-18
I've found that simply renaming the file from example.img to example.iso does the trick.

---

### Post by Absorbed on 2007-08-01
You can mount .img files:

```
mount -o loop blah.img /some/folder/ 
```

---

### Post by atomkarinca on 2007-08-01
you can try acetoneiso2: [http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

it has a nice gui and supports a lot of filetypes.

---

### Post by asmoore82 on 2007-08-01
'file' is a command line utitlity that identifies filetypes and is NOT fooled by extensions...

open a term and type 'file ' with the space at the end and then click and drag your
IMG file to that terminal and press enter in that terminal.

```
~ $ file '/home/asmoore/iso/pclinuxos-2007.img' 
/home/asmoore/iso/pclinuxos-2007.img: ISO 9660 CD-ROM filesystem data
UDF filesystem data (unknown version, id 'NSR01') '20070518                       '
(bootable)
```

if 'file' says it's an ISO it's an ISO and can be renamed

here's file on a bootable mac CD image that i renamed to iso ... not fooled

```
~ $ file '/home/asmoore/iso/norton-utilities-8.0-mac.iso'
/home/asmoore/iso/norton-utilities-8.0-mac.iso: Apple Partition data
block size: 2048, first type: Apple_partition_map, name: Apple,
number of blocks: 63, second type: Apple_Driver43, name: Macintosh,
number of blocks: 56, third type: Apple_Void, name: , number of blocks: 0,
fourth type: Apple_Driver_ATAPI, name: Macintosh, number of blocks: 56
```

and for those among you who may doubt file's Super Penguin Powers ...
```
~ $ sudo dd bs=512 count=1 if=/dev/sda of=sda.txt 
Password:
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0340878 seconds, 15.0 kB/s
asmoore@asmoore-laptop:~$ file sda.txt
```

:KS What does file say ?? ( you may need to change all 'sda' to 'hda' for IDE hard drives )

P.S. you will later require root privy to delete your "Text" file ... **~ $ sudo /bin/rm sda.txt**

---

### Post by altonbr on 2008-01-05
> **asmoore82 said:**
> 'file' is a command line utitlity that identifies filetypes and is NOT fooled by extensions...

open a term and type 'file ' with the space at the end and then click and drag your
IMG file to that terminal and press enter in that terminal.

```
~ $ file '/home/asmoore/iso/pclinuxos-2007.img' 
/home/asmoore/iso/pclinuxos-2007.img: ISO 9660 CD-ROM filesystem data
UDF filesystem data (unknown version, id 'NSR01') '20070518                       '
(bootable)
```

if 'file' says it's an ISO it's an ISO and can be renamed

here's file on a bootable mac CD image that i renamed to iso ... not fooled

```
~ $ file '/home/asmoore/iso/norton-utilities-8.0-mac.iso'
/home/asmoore/iso/norton-utilities-8.0-mac.iso: Apple Partition data
block size: 2048, first type: Apple_partition_map, name: Apple,
number of blocks: 63, second type: Apple_Driver43, name: Macintosh,
number of blocks: 56, third type: Apple_Void, name: , number of blocks: 0,
fourth type: Apple_Driver_ATAPI, name: Macintosh, number of blocks: 56
```

and for those among you who may doubt file's Super Penguin Powers ...
```
~ $ sudo dd bs=512 count=1 if=/dev/sda of=sda.txt 
Password:
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0340878 seconds, 15.0 kB/s
asmoore@asmoore-laptop:~$ file sda.txt
```

:KS What does file say ?? ( you may need to change all 'sda' to 'hda' for IDE hard drives )

P.S. you will later require root privy to delete your "Text" file ... **~ $ sudo /bin/rm sda.txt**

Very useful, thanks! Ill use 'file' a lot more often now.

For those of you who want to convert an img file to iso, it's not via img2iso but rather ccd2iso (Feisty-Hardy):
> $ sudo aptitude install ccd2iso
$ ccd2iso $img_file $iso_file
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=2iso&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=2iso&searchon=names&subword=1&version=all&release=all)

---

### Post by rare HERO on 2008-02-23
Seems like that last post worked, thanks.

---

### Post by Rohen on 2008-05-20
After hours and hours of messing around with VirtualBox... I finally got it working.  I'm installing XP as I write this...

PHEW

---

### Post by muniak on 2008-06-15
> **lazyart said:**
> It's not in the repositories... that's why you'd have to build it yourself.

[http://www.t2-project.org/packages/img2iso.html](http://www.t2-project.org/packages/img2iso.html)

This worked perfect for me. Thanks a lot!

---

### Post by altonbr on 2008-06-16
> **muniak said:**
> This worked perfect for me. Thanks a lot!

I said above that you can use ccd2iso in the commandline as it is included with Ubuntu, but whatever works for you!

---

### Post by chaosfinity on 2008-07-06
Hate to bring up an old thread but there is another program to use for this its all2iso converts many types of images to iso including img and uif [http://gnu.ethz.ch/debian/all2iso/](http://gnu.ethz.ch/debian/all2iso/)

---

