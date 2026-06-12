---
title: "how to define root for FAT32??"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by thunderkyss on 2007-05-27
I'm trying to partition my data drive. I want it to be FAT32, so I can use it, wether I'm in Ubuntu or XP. I keep getting an error, saying "no root files system is defined"


I told it, that I want a FAT32 partition. I've tried doing it as a Primary drive, and a logical drive. I've tried to define the mount point as /, /dos, & /windows, default mount options, and bootable flag on & off, and it keeps giving me the same error.


Any ideas??

---

### Post by taurus on 2007-05-27
Are you trying to install Ubuntu on a fat32 filesystem?

---

### Post by thunderkyss on 2007-05-27
no, Ubuntu is already isntalled on another hard disk. This is a second disk in the computer that is presently NTFS, but I want to erase it, and make it FAT32.

---

### Post by taurus on 2007-05-27
Are you converting ntfs to vfat with gparted (in Ubuntu)?

---

### Post by thunderkyss on 2007-05-27
at the present time, I can't boot into ubuntu.

I'm trying to figure that out as well. 

But I've got the ubuntu install disk, and there is a part of the install process that formats the drives, so I figured I'd handle it here.


I'm not trying to install Ubuntu, I was just going to see If I could install the grub bootloader without installing Ubuntu.

---

### Post by taurus on 2007-05-27
The best way is to get Ubuntu running first.  Then, install gparted and use it to reformat your partition from ntfs to vfat.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

Otherwise, use gparted on the LiveCD, System -> Administration, and convert it if you wish.  Don't install it since it will look for / and swap again.  Use gparted on the LiveCD instead.

---

### Post by eentonig on 2007-05-27
What I'm thinking is, that you screwed up big time.

You said you created that FAT32 partition and mounted it on '/', If this succeeded, it would have removed your old '/' mount, which is where your Ubuntu installation was running from.

---

### Post by freebird54 on 2007-05-27
An alternative is, rather than work from the 'install' of Ubuntu, just run the GPartEd (Gnome Partition Editor) directly from the Live CD session.  It should be under System->Administration->Gnome Partition Editor.

When you are trying from the install session, it it insisting that Ubuntu needs a / (root) partition to be created so that it can install.... not what you're intending I would gather.

How is your Ubuntu failing to work at the moment?  Did it work?  Have you changed the 'apparent order' of the drives in the BIOS while working on this other one?  Let us know what's happening - we are here to fix!

---

### Post by thunderkyss on 2007-05-27
> **freebird54 said:**
> An alternative is, rather than work from the 'install' of Ubuntu, just run the GPartEd (Gnome Partition Editor) directly from the Live CD session.  It should be under System->Administration->Gnome Partition Editor.

Hey, that worked great.....

Ubuntu is working fine. So far, I have  had no problems with Ubuntu itself. 

Right now, my issue is with the GRUB installer. 

The first time I installed Ubuntu, I installed to my second harddrive, which i normally used for audio data. but I figured I'd try Ubuntu there, since it was basically clean.

I liked Ubuntu, and tried to figure a more permanent installation scheme. 

I'm running xp64 Pro, and decided to do a fresh install of that as well. 

But I'm also testing 64studio..... so I figured, I'll put the three OS's on my main drive(150G), then record all my audio to my audio drive(250G)... 

So, I installed Ubuntu first, then 64 Studio, then XP64. I'd probably had been ok, if I'd have installed anything but XP last, since XP doesn't try to load a boot manager.

---

### Post by freebird54 on 2007-05-27
Definitely the worst order!  However - all is not lost :)

Here is a link [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) that might help you re-install grub so that all will be recognized and accessible at boot.  OR- you could re-install Ubuntu if you haven't got too much 'done' on it so far, - and it will see the other OS's, install grub, and write the boot entries for you.  Your choice - slow, but it's done for you - or learn how to do it quickly  :)

Enjoy!

---

### Post by thunderkyss on 2007-05-27
I'm going to reinstall Ubuntu..

just out of curiosity..... how big should a swap file be??

---

### Post by freebird54 on 2007-05-27
You will hear 1.5 times RAM and 2 times RAM - but I figure it depends on how much RAM you have!  I have 512Mb and I rarely hit the swap file, so I suspect that the 1 Gb I gave it is more than sufficient.  If you have 1Gb RAM, I doubt you'll ever need it at all!  But - give a Gb or so - HD space is cheap now... :)

---

