---
title: "2 hard drive dual boot, without changing MBR"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by slampy on 2007-08-02
hi there, I've been drifting in and out of linux for a while now, but my last effort resulted in my windows HDD getting messed up with the master boot record.  I have two HDDs, one with windows, and other one for linux.  I want to start fresh again with linux, so is there a way I can dual boot without changing the MBR?  I'd love it if I can do such a thing.  maybe I can use removable drives or something.  I'm not sure.  I just do not want to alter my windows HDD this time because I'm not quite nerdy enough to fix it when I screw up the mbr.  but I am pretty computer oriented, so I'm sure if there's a way to do this I'll be able to figure it out, I just need someone's help.  thanks!

---

### Post by ayenack on 2007-08-02
Take a look at [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Boot_Ubuntu_from_the_Windows_Bootloader") Might help. Also check out the bit above [Super Grub]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Super_Grub_Disk").

It really should not be an issue to install Ubuntu alongside Win XP or any other Windows OS's as long as you know where your Windows drives/partitions are.

---

### Post by dannyboy79 on 2007-08-02
> **slampy said:**
> hi there, I've been drifting in and out of linux for a while now, but my last effort resulted in my windows HDD getting messed up with the master boot record.  I have two HDDs, one with windows, and other one for linux.  I want to start fresh again with linux, so is there a way I can dual boot without changing the MBR?  I'd love it if I can do such a thing.  maybe I can use removable drives or something.  I'm not sure.  I just do not want to alter my windows HDD this time because I'm not quite nerdy enough to fix it when I screw up the mbr.  but I am pretty computer oriented, so I'm sure if there's a way to do this I'll be able to figure it out, I just need someone's help.  thanks!


yes, you can merely install grub onto your Ubuntu hard disk instead of your windows drive. If you bios permits, you'll want to make sure that your bios has the  ubuntu drive (where grub will be in the mbr) FRIST and teh windows drive second. some bios's don't permit this and you may need to rearrange the disks within your case. I always use master and slave NOT cable select.

With this though, windows doesn't like being booted from a non first disk, you'll need to use the map options within your windows grub boot entry like the following:

title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by ayenack on 2007-08-02
It's possible just edit the Windows boot.ini to include Ubuntu and not have to change anything else... I believe? You simply point Windows to the Ubuntu boot drive/partition. Select the advanced option on the last page of the install process of Ubuntu and select your ubuntu drive rather than your XP drive then edit your Win boot.ini to include your Ubuntu drive. I've never done this so I may be wrong but I think this is correct.

Are you using XP or Vista?

---

### Post by Frak on 2007-08-02
Have you ever Tried [Wubi]("http://wubi-installer.org/")? I think it would save you alot of trouble, by having Ubuntu base within Windows. It alters boot.ini so you can boot the Ubuntu file.

---

### Post by dannyboy79 on 2007-08-02
> **ayenack said:**
> It's possible just edit the Windows boot.ini to include Ubuntu and not have to change anything else... I believe? You simply point Windows to the Ubuntu boot drive/partition. Select the advanced option on the last page of the install process of Ubuntu and select your ubuntu drive rather than your XP drive then edit your Win boot.ini to include your Ubuntu drive. I've never done this so I may be wrong but I think this is correct.

Are you using XP or Vista?
that won't work. what you're suggesting is using NTLDR to boot Ubuntu. It can BUT you have to create a image of your boot sector of that Ubuntu disk and save it on your windows computer and update your boot.ini to point to that. Basically what the post above mine already said but I am guessing you missed it because you didn't read the link he posted.

---

### Post by ayenack on 2007-08-02
Just read Frak post that seems like a reasonable choice. I've never had an issue with dual boots but have seen a lot of post by people saying they have lost their XP partitions after installing Ubuntu and not quite been able to workout why.

I realise now that the "dd if=/dev/sda2 of=~/Desktop/Ubuntu.mbr bs=512 count=1" part of the wiki that I posted is basically that. Copying the Ubutu MBR to Win boot.ini. This is what I meant to say in my tongue twisted way.

---

### Post by dannyboy79 on 2007-08-02
> **ayenack said:**
> Just read Frak post that seems like a reasonable choice. I've never had an issue with dual boots but have seen a lot of post by people saying they have lost their XP partitions after installing Ubuntu and not quite been able to workout why.

I realise now that the "dd if=/dev/sda2 of=~/Desktop/Ubuntu.mbr bs=512 count=1" part of the wiki that I posted is basically that. Copying the Ubutu MBR to Win boot.ini. This is what I meant to say in my tongue twisted way.
no. what it does is copies the boot sector of the Ubuntu installed hard drive to an image or file. then you open the boot.ini file within a text editor and add an entry pointing to that image or file that contains the Ubuntu boot sector. 

I am sure you keep meaning to say this but I just want to be clear for newbies and what not.

---

### Post by ayenack on 2007-08-02
You say what i want to say... and also help to clarify it in my mind. Should not have had those beers this afternoon:biggrin:

---

