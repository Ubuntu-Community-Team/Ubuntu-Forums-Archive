---
title: "Best format for sharing memory stick between mac and linux?"
date: 2014-11-18
forum: Apple Hardware Users
---

### Post by zircon_34 on 2014-11-18
What format do you use for best compatibility between Mac OSX and Ubuntu? Is there a way to use an encrypted memory stick on both OSs?

I tried to format my memory stick in EXT4 in Ubuntu 14.04 Gnome or in mac and use it in both OSs, but this did not work. The main problem was that when I formatted the stick in mac and tried to open it in linux, the permission was read only, so I could not add files to the stick. I tried to change file permissions using 

```
sudo nautilus
```

But access was denied. So I formatted the stick using Gparted and tried to open it in Mac OSX, but it did not recognize the format.

The only format that worked for both was FAT but the problem is that the max size of files transferable is constrained.

---

### Post by xmbwd on 2014-11-19
The best way to go is exFAT.  Then after that, FAT32.

---

### Post by Lars Noodén on 2014-11-20
fat and xfat  are both good for losing data, they are not robust and the larger the file system, the greater the risk that it picks up an error.  It also does not support file permission, etc. and all that would be lost with any files transferred to a FAT partition.  So I'd call that absolute last resort.  

OS X uses HFS+ with journalling.  Ubuntu reads that just fine, as you've seen.  But it does have trouble with the journalling, but will both read and write just fine with the journalling turned off on your USB stick.  I used that myself for years for my transfers between OS X and Ubuntu and found it to work well.  Just use the Disk Utility in OS X to turn off journalling for that stick and it should subsequently be writeable in Ubuntu, too.

---

### Post by Morbius1 on 2014-11-20
This is more of an FYI ...........

OSX allows a write to an ntfs partition natively.

What OSX doesn't do is automount the usb stick that way.

You can if you so desire circumvent that using this technique: [http://computers.tutsplus.com/tutorials/quick-tip-how-to-write-to-ntfs-drives-in-os-x-mavericks--cms-21434](http://computers.tutsplus.com/tutorials/quick-tip-how-to-write-to-ntfs-drives-in-os-x-mavericks--cms-21434)

It also works in Yosemite in case you updated.

Notes:

*** This will only make sense if we are talking about a specific usb device rather that .just a random one you have on hand at the moment.
*** And it also helps if you are the owner of the aforementioned OSX machine
*** If you go down this route don't be surprised when you open /etc/fstab in OSX and find it empty. It doesn't use fstab to mount the system partition. Linux doesn't have to either but that's another topic.

---

### Post by zircon_34 on 2014-11-23
> **Lars Noodén said:**
> fat and xfat  are both good for losing data, they are not robust and the larger the file system, the greater the risk that it picks up an error.  It also does not support file permission, etc. and all that would be lost with any files transferred to a FAT partition.  So I'd call that absolute last resort.  

OS X uses HFS+ with journalling.  Ubuntu reads that just fine, as you've seen.  But it does have trouble with the journalling, but will both read and write just fine with the journalling turned off on your USB stick.  I used that myself for years for my transfers between OS X and Ubuntu and found it to work well.  Just use the Disk Utility in OS X to turn off journalling for that stick and it should subsequently be writeable in Ubuntu, too.
Thanks, I will try this!

---

### Post by d4m1r on 2014-11-24
I would say plain old NTFS....It might not be native to either OS but then it guarantees it would work with other devices after the fact like a WDTV, Windows based PC, etc.

Under Ubuntu, NTFS is a little slow and under OS X you have to install a 3rd party application (like Tuxera) but I can confirm I have 1 16GB USB (for example) NTFS formatted, and then it can be read/copy/cut/pasted to by all 3 OS'. Windows, OS X, and Ubuntu.

---

### Post by Morbius1 on 2014-11-24
> **d4m1r said:**
> ... and under OS X you have to install a 3rd party application (like Tuxera) 
OSX can write to an ntfs partition natively without requiring any 3rd party software. It just doesn't do it automatically.

** Create an /etc/fstab file in OSX
** Add a line defining the ntfs partition to be mounted - for a USB device it would be something like:
```
LABEL=NTFSDriv*e* none ntfs rw,auto,nobrowse


```
And the next time the drive is inserted it will be at /Volumes/NTFSDrive fully writeable.

---

### Post by zircon_34 on 2014-11-24
But NTFS is proprietary... right?

---

### Post by carlwsnyder on 2014-11-25
> **zircon_34 said:**
> But NTFS is proprietary... right?
That is correct.  So are FAT, xFAT, FAT32, and HFS/HFS+ file systems.  Windows and Mac OS X don't work properly with any non-proprietary file system.  Why should they?

---

### Post by Lars Noodén on 2014-11-26
Actually, [HFS/HFS+ is open source](http://www.opensource.apple.com/source/hfs/hfs-285/) and under the OSI-approved [Apple Public Source](http://opensource.org/licenses/alphabetical) license.  They're finding ways to lock users in and take away control, but much of OS X, albeit an apparently diminishing portion, is free and open source, being based on Darwin and including a lot of GNU.  But, yeah, OS X works poorly with EXT, that is to say, not at all.  So HFS+ it is and without journalling until becomes available.

---

### Post by zircon_34 on 2014-11-26
I tried to write to an NTFS hard drive on MacOSX a while back and it was just not possible, same thing at work. I thought thats an unnecessary pain. Would be neat to list which file system is faster to use in both OSX and linux. Don't know if someone tested this....

---

### Post by zircon_34 on 2014-11-26
[http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1)

---

### Post by Morbius1 on 2014-11-27
You couldn't write to an ntfs partition in OSX because you didn't read my posts or better yet the HowTo I linked to above.

Anyhoo, It would appear that your solution given the full set of requirements you specified above is quite simple:

Remove OSX from the mac.
Replace it with Ubuntu.
Format your USB device to ext4.

You will of course have some continuing permissions issues by doing this unless you:

*** Make sure both users on each machine have exactly the same user name and more importantly the same uid.
OR
*** Assume that each user has sudo privileges to reset the permissions.
OR
*** Use bindfs against each users /media/$USER directory setting the owner to that user so it won't matter what the Linux permissions are on the device itself. Every time you plug in the device it will be owned by that user sorta kinda like the way it works when you plug in something formatted to ntfs.

---

### Post by Lars Noodén on 2014-11-27
Again, you can format the stick for HFS+ using OS X and turn of the journalling for the stick.  Then you can read and write it in both Ubuntu and OS X.  

Or, if you install the packages hfsplus, hfsprogs and hfsutils, you can use gparted to create the partition in Ubuntu without the need for OS X.  

But as Morbius1 points out, user onwership of the files will haunt you regardless of whether you use HFS+ or EXT.  When I ran OS X, I used to sync the OS X  user ids to the ones I had on Ubuntu.

---

