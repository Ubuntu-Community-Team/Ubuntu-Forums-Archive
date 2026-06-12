---
title: "Is it possible to install or use XP in ext2\3?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Shadix on 2006-06-27
I've been reading around about NTFS's huge flaws when it comes to writing to the partitions and I was wondering if there is a way to not use NTFS at all and maintain a Windows installation using a completely different filesystem.

I'm trying to set up a dualboot system where the majority of my data is in Linux.



I'd imagine a possible scenario would be by installing the FS driver in Windows, copying all the files over to Ubuntu for temporary storage, formatting the NTFS partition into an EXT2 partition, copying the files back over, and configuring Grub so it tries to boot windows.  However it feels like something is missing (and I don't want to try this until I'm sure how to make it work).

---

### Post by Lord Illidan on 2006-06-27
I doubt you can make it.

However, why not use FAT? It can be read and written to by both OSes.

---

### Post by MaximB on 2006-06-27
I don't recommand you to do that....it's riscy...and I don't know how can you install the ext2/3 drive before moving winxp to this partition...don't think it's possible.
just leave the winxp partition alone and convert all other partitions to ext3 like I did.
it's the best choice.

---

### Post by Lord Illidan on 2006-06-27
Just install XP on a FAT partition instead of NTFS.

---

### Post by Shadix on 2006-06-27
The problem with FAT is that the partition in question is quite large (178GB) and the file size limit is pathetic.


I also don't recall the XP installation having an option to format to FAT... :\

I seriously don't see how this is risky..  If it works it works if it doesn't I delete the partition in Ubuntu and go on with my day.  The absolute worse case scenario is that I'd have to format my entire HDD again, which would NOT be that big of a deal considering I've only had Ubuntu set up for a few days now.


Maybe I posted this in the wrong forum.

---

### Post by glinsvad on 2006-06-27
Create a smaller (~10GB) FAT32 partition to house the XP install and other programs, a large (~168GB) ext3 partition for your data and mount the ext3-partition in XP using [this]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm") driver.

On the upside, this larger partition can then be read/write-shared between Linux and XP - superb! I use this setup for sharing email, favorites and documents because I also run Firefox and Thunderbird under XP :D

EDIT: Brainfreeze... there's no need to make your XP partition FAT32 if you don't want to access program/installation files from within Linux, so just make XP run on NTFS as usual.

---

### Post by Shadix on 2006-06-27
I'll try that, but is there a way to reinstall my XP without destroying GRUB?\

---

### Post by loserboy on 2006-06-27
I dunno i was wondering the same thing, but can't you just re-install grub from like super grub disc or something

---

### Post by glinsvad on 2006-06-27
Yes and no. Installing XP will destroy GRUB, but it can easily be restored.

Check out [this]("http://www.ubuntuforums.org/showthread.php?t=24113") thread.

Also, the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation") describes how.

---

### Post by FuzZy2006 on 2006-06-27
you can use win4lin or vmware to virtually instal windows on linux

---

### Post by Shadix on 2006-06-27
Interesting...  I thought you had to have installed Windows already in order to use VMWare for Linux.  I need to do a physical installation for games and stuff, as I doubt VMWare is as efficient as running the real deal.


Thanks glinsvad for all the help.

Edit:  that is actually what I intended to do is run my physical installation through VMWare, but I don't know if that is possible if it is in NTFS.

---

### Post by aysiu on 2006-06-27
In my experience, VMWare slows down Windows considerably, but for some strange reason seems to run at native speeds in Ubuntu.

Again--only my experience.

Of course, you can't have five other applications sucking up memory while you're running VMWare...

---

