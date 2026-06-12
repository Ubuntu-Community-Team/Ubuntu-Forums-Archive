---
title: "[SOLVED] Fat partition not mounting on mac OSX"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by albesan on 2008-12-04
Hello team,

I'm on a MacBook running intrepid 64 bit.
I partitioned the internal drive using Gparted live CD.
I created two new partitions one ext3 one Fat in addition to the Mac OSX one.
So the idea was to have a Mac OSX partition, a ext3 with ubuntu and a Fat partition accessible from both systems that I could use as storage.

Everything works fine on the ubuntu side but I can't mount the Fat partition on mac osX.

I might be missing something really obvious, I'm new to the macintel side of things and I don't quite understand it yet.

I've been searching on google but haven't managed to find any similar issues.

Any comments appreciated


Regards


a.

---

### Post by pxwpxw on 2008-12-04
> **albesan said:**
> Hello team,

I'm on a MacBook running intrepid 64 bit.
I partitioned the internal drive using Gparted live CD.
I created two new partitions one ext3 one Fat in addition to the Mac OSX one.
So the idea was to have a Mac OSX partition, a ext3 with ubuntu and a Fat partition accessible from both systems that I could use as storage.

Everything works fine on the ubuntu side but I can't mount the Fat partition on mac osX.

I might be missing something really obvious, I'm new to the macintel side of things and I don't quite understand it yet.

I've been searching on google but haven't managed to find any similar issues.

Any comments appreciated


Regards


a.

I get the same result when using the ubuntu installer gparted, and this is my explanation and solution.

The problem comes from formatting the msdos FAT partition with Gparted and not Macosx.
Gparted sets a flag (msftres) for msdos partitons , Macosx sees this and wont automount.
You can manually mount from a Macosx terminal -
```

$ cd
$ diskuti list 
///// say its on disk0s5
$ mkdir xxx
$ sudo mount -t msdos /dev/disk0s5 xxx

```
(msdos=FATxx)
Then open xxx with finder widow from your home directory.

To get the partition automounting, use the macosx Diskutility to erase that partition back to msdos.
You might have to unmount it.
Then it should mount, as long as you keep gparted away from it.

Doing this from memory, thats the outline.

---

### Post by albesan on 2008-12-04
> **pxwpxw said:**
> I get the same result when using the ubuntu installer gparted, and this is my explanation and solution.

The problem comes from formatting the msdos FAT partition with Gparted and not Macosx.
Gparted sets a flag (msftres) for msdos partitons , Macosx sees this and wont automount.
You can manually mount from a Macosx terminal -
```

$ cd
$ diskuti list 
///// say its on disk0s5
$ mkdir xxx
$ sudo mount -t msdos /dev/disk0s5 xxx

```
(msdos=FATxx)
Then open xxx with finder widow from your home directory.

To get the partition automounting, use the macosx Diskutility to erase that partition back to msdos.
You might have to unmount it.
Then it should mount, as long as you keep gparted away from it.

Doing this from memory, thats the outline.

hey, thanks for the reply.

I tried erasing the partition from mac osx as you suggested but it did not work. 
Now it does not mount on either os.

I can see it on gparted from ubuntu but I can see that mac osx has assigned it the msftres label.

I don't get it, I thought the problem was with gparted assigning such a label to the partition.

Thanks anyway, if you think of a way of sorting this out let me know.

Wouldn't it be possible to change the labe from gparted? if so what would the appropriate label be?

thanks

a.

---

### Post by pxwpxw on 2008-12-04
Oh ok, maybe I had to create it with macosx in the first place. It is the flag that is the villain. I'll recheck that tomorrow.
But did you try the manual mount.
You cant get rid of it in parted/gparted - it just toggles from msftres to boot and back, its like the plague once you have got it.

---

### Post by cyberdork33 on 2008-12-04
> **pxwpxw said:**
> Oh ok, maybe I had to create it with macosx in the first place. It is the flag that is the villain. I'll recheck that tomorrow.
Yes, I tend to recommend creating your FAT partition with DiskUtility, then installing Ubuntu with it's tools. This ensures that it is accessible from both systems.
> **pxwpxw said:**
> You cant get rid of it in parted/gparted - it just toggles from msftres to boot and back, its like the plague once you have got it.

Nope, it is a bug.
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

---

### Post by pxwpxw on 2008-12-04
> **cyberdork33 said:**
> Yes, I tend to recommend creating your FAT partition with DiskUtility, then installing Ubuntu with it's tools. This ensures that it is accessible from both systems.


Nope, it is a bug.
[http://www.macosxhints.com/article.php?story=20080130022147512](http://www.macosxhints.com/article.php?story=20080130022147512)

Glad its only a bug.:o

Yes that ref is a good explanation, but the bottom line is that I thought the manual mount (command line) worked, I have to recheck it.

---

### Post by pxwpxw on 2008-12-05
Not so easy.

I tried erasing FAT32 in Macosx to remove the unwanted msftre flag from parted.
1. I can aalways mount the partiition -t msdos manually.
2. I cant do anything with a vfat msdos partition if its on the boot drive.
3. I can erase it using diskutil, (the GUI) if its on an external, then it mounts.
4. I can erase it on the internal drive using an external Macosx.
Then it mounts.

So it should be possible to erase the flag using the Disk Utiity when booted from the Macosx install DVD, and then it should  mount.

---

### Post by albesan on 2008-12-05
> **pxwpxw said:**
> Not so easy.

I tried erasing FAT32 in Macosx to remove the unwanted msftre flag from parted.
1. I can aalways mount the partiition -t msdos manually.
2. I cant do anything with a vfat msdos partition if its on the boot drive.
3. I can erase it using diskutil, (the GUI) if its on an external, then it mounts.
4. I can erase it on the internal drive using an external Macosx.
Then it mounts.

So it should be possible to erase the flag using the Disk Utiity when booted from the Macosx install DVD, and then it should  mount.

hey,
Thanks for the input everybody.

I tried booting from mac osx cd and erase the partition with disk utility but it didn't work either, I got the same results as when trying to do it from the internal mac osx.

cyberdork33 so how do would you advice to go about doing this partitioning?
From mac osx with disc utility?
I'm cosidering rebuilding the whole system.
Any advice welcome.

thanks

a

---

### Post by iphonegames on 2008-12-05
lol. Check my new [iphone games](http://www.iphonegames3g.com) site for iphone and ipod touch when you have time! :)

---

### Post by cyberdork33 on 2008-12-06
> **albesan said:**
> cyberdork33 so how do would you advice to go about doing this partitioning?
From mac osx with disc utility?
yep.
For you, I would recommend Creating our OSX HFS+ partition, and two msdos partitions. (one is space for  storage, the other will be replaced by Ubuntu).

Then boot the Ubuntu LiveCD and use gparted to delete one of the msdos partitions leaving free space. Then start the installer and when prompted, choose to install to the "largest free space" and the installer will create a root / swap partition for you.

I am sure the partition is mountable manually the way you did it, but it is a little annoying that it is not automatic. Of course you could add it to /etc/fstab

---

### Post by albesan on 2008-12-06
Hey, thanks for the reply.

> **cyberdork33 said:**
> yep.
For you, I would recommend Creating our OSX HFS+ partition, and two msdos partitions. (one is space for  storage, the other will be replaced by Ubuntu).

Then boot the Ubuntu LiveCD and use gparted to delete one of the msdos partitions leaving free space. Then start the installer and when prompted, choose to install to the "largest free space" and the installer will create a root / swap partition for you.


Must I do it this way? Would it be a problem to specify what partition I want ubuntu to go in? 
It is just that I'm planning to have a larger partition for storage.
I'm finding Mac OSX quite picky with partitions and I just don't want to rebuild the whole thing and find out it doesn't work.


> 
I am sure the partition is mountable manually the way you did it, but it is a little annoying that it is not automatic. Of course you could add it to /etc/fstab

Yes I can mount the partition manually on Ubuntu but I can't do it on mac osx.


Thanks again.

a.

---

### Post by albesan on 2008-12-06
Hey, thanks for the reply.

> **cyberdork33 said:**
> yep.
For you, I would recommend Creating our OSX HFS+ partition, and two msdos partitions. (one is space for  storage, the other will be replaced by Ubuntu).

Then boot the Ubuntu LiveCD and use gparted to delete one of the msdos partitions leaving free space. Then start the installer and when prompted, choose to install to the "largest free space" and the installer will create a root / swap partition for you.


Must I do it this way? Would it be a problem to specify what partition I want ubuntu to go in? 
It is just that I'm planning to have a larger partition for storage.
I'm finding Mac OSX quite picky with partitions and I just don't want to rebuild the whole thing and find out it doesn't work.


> 
I am sure the partition is mountable manually the way you did it, but it is a little annoying that it is not automatic. Of course you could add it to /etc/fstab

Yes I can mount the partition manually on Ubuntu but I can't do it on mac osx.


Thanks again.

a.

---

### Post by cyberdork33 on 2008-12-06
> **albesan said:**
> Must I do it this way? Would it be a problem to specify what partition I want ubuntu to go in? 
It is just that I'm planning to have a larger partition for storage.
I'm finding Mac OSX quite picky with partitions and I just don't want to rebuild the whole thing and find out it doesn't work.
You don't _have_ to do it that way, it is just the easiest way IMO. I don't understand why it is a bad way to do it according to the rest of the info you have though. You just allocate the partition space that you want to use for Ubuntu upfront. You can make any of the partitions any size you want. For example, if you want a large storage partition:

1. EFI (hidden in Disk Utility)
2. OSX
3. 100GB msdos partition for storage
4. 10GB temporary msdos partition for Ubuntu

Then you delete partition 4 in gparted and run the installer indicating that you want it to install in the free space.

---

### Post by pxwpxw on 2008-12-06
For the shared storage, I don't see why a msdos fat32 partition should be necessary or even desirable, given that access is only wanted from Macosx and ubuntu.

An hfsplus partition (macos extended but not journalled) is read/write accessible from both and can be created from Macosx, it is the Macosx preferred format. It may be necessary to set the macosx permissions to read/write, but that is easily done from macosx.

I use that configuration, I have not found any problem with it, use it for common access.
Of course it is not suitable for Windows.

---

### Post by cyberdork33 on 2008-12-06
> **pxwpxw said:**
> For the shared storage, I don't see why a msdos fat32 partition should be necessary or even desirable, given that access is only wanted from Macosx and ubuntu.

An hfsplus partition (macos extended but not journalled) is read/write accessible from both and can be created from Macosx, it is the Macosx preferred format. It may be necessary to set the macosx permissions to read/write, but that is easily done from macosx.

I use that configuration, I have not found any problem with it, use it for common access.
Of course it is not suitable for Windows.

really none of the options are ideal... no journalling with hfs+, fat32 is just old and insecure, ntfs is an OK option but relies on FUSE, and the ext3 driver for OSX is dead.

---

### Post by pxwpxw on 2008-12-06
I didn't know macosx could do ntfs. I just find  the hfs+ option is easiest to do and use in a Mcosx/ubuntu context.

---

### Post by albesan on 2008-12-09
> **pxwpxw said:**
> For the shared storage, I don't see why a msdos fat32 partition should be necessary or even desirable, given that access is only wanted from Macosx and ubuntu.

An hfsplus partition (macos extended but not journalled) is read/write accessible from both and can be created from Macosx, it is the Macosx preferred format. It may be necessary to set the macosx permissions to read/write, but that is easily done from macosx.

I use that configuration, I have not found any problem with it, use it for common access.
Of course it is not suitable for Windows.

Hey thanks for the replies.

Like I said I'm new to the ubuntu on a mac.
I was just trying to replicate my old pc set up on this new mac.
I assume fat was the most versatile formating for a shared partition.

Anyways I followed cyberdorks advice (thanks very much cyberdork) and managed to rebuild the system and now the fat partition mounts on both systems.

I had some side effects though, I've been trying to solve them without much luck but I think it has to do with the way I backed up my ubuntu.

I've opened another thread about it 'cos it seems off topic for this one:

[http://ubuntuforums.org/showthread.php?t=1006369](http://ubuntuforums.org/showthread.php?t=1006369)  


Again if you get a chance to take a look at it and have any ideas/have run into this before any input would be greatly appreciated.


Thanks again for your help.

regards


a.

---

