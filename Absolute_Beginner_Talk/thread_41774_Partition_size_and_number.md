---
title: "Partition size and number"
date: 2005-06-14
forum: Absolute Beginner Talk
---

### Post by Moosferatu on 2005-06-14
I'll be getting a new laptop soon with a 80gig hard drive and 512megs of memory.  Like most everyone else, I want to duel-boot with XP.  My question is how many partitions should I make, and how big should they be?

I've read a couple places that the swap partition should be twice the amount of memory.  Should I make it a gig?  That seems like a lot.  I also read somewhere that the Ubuntu installation takes just under 2gigs.  What I haven't been able to figure out is if people leave Ubuntu isolated in the root partition and make another partition for programs to be installed to, or if it all just goes under the root.  Finally, I want to make a partition for shared files, and was thinking about making it 20 or 30 gigs.  Is that too much?  The rest I figured I'd leave for XP.


[Sidenote]The font this forum uses is awesome. [IMG]http://www.idlethumbs.net/images/thumbsup.gif[/IMG]

---

### Post by aysiu on 2005-06-14
If you have 512 MB RAM, you don't need a swap partition at all. If you make one, it'll never be used. With 80 GB, this is what I would advise:

1. When you get the laptop, install all the Windows applications you need (and uninstall the ones you don't need), but don't put any files on it (images, pictures, documents, music). See how much space Windows takes up. My guess is it'll be around 7 GB. So I'd leave another 3 for an even 10 GB, just in case you ever wanted to install more apps for XP.
2. Then defragment your hard drive and use something to resize the partition. This can be Partition Magic. I've used Mandriva's partitioning tool, and it's great. Mepis has one as well that's okay (QTParted). I wouldn't use Ubuntu to partition.
3. After you've resized the Windows partition (which should be NTFS if it's XP), create a large partition for your files (say, 60 GB) in FAT32 filesystem format.
4. Then, create a 10 GB partition in EXT3 filesystem format for Ubuntu. This should be mounted as / when you install Ubuntu. You can also, during the Ubuntu install process, choose to mount the Windows FAT partition as /windows or /media/windows.

So, the breakdown:

hda1 C: 10 GB (Windows NTFS)
hda2 D: 60 GB (Windows FAT)
hda3 10 GB (Ubuntu EXT3)

Put all your files in the FAT partition.

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=aysiu]If you have 512 MB RAM, you don't need a swap partition at all. If you make one, it'll never be used. With 80 GB, this is what I would advise:

1. When you get the laptop, install all the Windows applications you need (and uninstall the ones you don't need), but don't put any files on it (images, pictures, documents, music). See how much space Windows takes up. My guess is it'll be around 7 GB. So I'd leave another 3 for an even 10 GB, just in case you ever wanted to install more apps for XP.[/QUOTE]
If you plan on installing games, you'll need much more than that. I'd make it at least 15 GB.

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=aysiu]If you have 512 MB RAM, you don't need a swap partition at all. If you make one, it'll never be used. With 80 GB, this is what I would advise:
[/QUOTE]

I agree with everything but this. I have 512 and I need my swap partition sometimes. But half a gig for swap should be fine.

---

### Post by Moosferatu on 2005-06-15
So, how about this:

C: 30GB
D: 40GB
U 9.5GB
swap .5GB

Is 9.5GB for Ubuntu needed?  It seems like most of the software that I'd be installing on it is relatively small.  I have no problem giving it 9.5GB, but I just don't want to give it that much only to ever use 5GB of it.

---

### Post by aysiu on 2005-06-15
Well, only you know how many applications you'll download for Windows and/or for Ubuntu.

---

### Post by Moosferatu on 2005-06-15
True, but could anyone give me an idea of how much space is typically used?

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=Moosferatu]True, but could anyone give me an idea of how much space is typically used?[/QUOTE]

My ubuntu isntall is currently 5 or so gigs. The minimum is much less.

---

