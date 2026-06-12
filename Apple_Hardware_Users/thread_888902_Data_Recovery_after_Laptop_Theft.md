---
title: "Data Recovery after Laptop Theft"
date: 2008-08-13
forum: Apple Hardware Users
---

### Post by ghostslinger on 2008-08-13
If this was solved in a previous thread, I'm sorry for wasting peoples' time but I did use the search button and google :)

A little backstory: basically, my girlfriend had her macbook stolen and she just got it back, but the bugger that took it deleted all her docs, pics, and iTunes music library.
I, being her 24/7 tech support jumped at the opportunity to try and help her.  Unfortunately, I have absolutely zero ideas on how to recover things with a Linux recovery cd (I have INSERT at the moment).  Is there anyone that might have any ideas on how to go about some basic recovery techniques?  Or perhaps describe how the Time Machine might work?  I'm a windows turned linux guy and I know  little about Macs (especially with leopard now).

Any help is most appreciated and thanks for reading this.

*edit*
the laptop is one of the newer intel processor models (she got it at the same time the original iphone came out, so I'm not sure what it is specifically in regards to model)

---

### Post by tamoneya on 2008-08-13
you should try to use testdisk.  You can use the ubuntu liveCD/installer and get it from the repositories.  Run these commands in terminal:```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```
Then have it scan the disk for any partitions or files.  After it finds them tell it to recover them to an external drive.  You do not want to try to recover them to the internal drive because you could by accident end up writing over some of the files you want to recover.

---

### Post by ghostslinger on 2008-08-13
so I could put a Hardy Heron Live image on a flash and just get testdisk from the repos and then see if there's anything salvagable?  and then back it up to an external drive?  Is it possible I could use a few dvds?  because I don't have a drive to spare right now x.X

I know I'm reiterating the instructions you gave me, but I really want her to get back everything she can and I'd hate to be the one to mess things up more.

Also, is there anything I should tell her in regards to keeping the laptop off until I can get testdisk running?  I've found a lot of people saying not to use a laptop that's waiting for recovery because files you are trying to rescue might get written over while the computer is in use.

---

### Post by cyberdork33 on 2008-08-13
> **ghostslinger said:**
> Or perhaps describe how the Time Machine might work?  I'm a windows turned linux guy and I know  little about Macs (especially with leopard now).
If she used Time Machine, she would have an external Hard drive or something with the backup on it, otherwise Time Machine is irrelevant.

> **ghostslinger said:**
> so I could put a Hardy Heron Live image on a flash and just get testdisk from the repos and then see if there's anything salvagable?  
no because the Macs won't boot from an external hard drive (not linux anyway).

> **ghostslinger said:**
> Also, is there anything I should tell her in regards to keeping the laptop off until I can get testdisk running?  I've found a lot of people saying not to use a laptop that's waiting for recovery because files you are trying to rescue might get written over while the computer is in use.
Um yea, definitely DO NOT use the machine. The data is there, the drive is just "marked" as empty. This means the OS will have no problem writing new data there. 

I don't know of any, but you might look for recovery apps that run IN OS X... I know, I know, heresy. Unfortunately I think that most of the Open Source tools won't help on an HFS+ filesystem...

---

### Post by ghostslinger on 2008-08-13
The recovery tools in OS X would be nice.  But I don't really want to pay.  Could I use an external drive I've got my old windows stuff backed up on and possibly create a partition that uses an HFS+ filesystem?

---

### Post by cyberdork33 on 2008-08-14
> **ghostslinger said:**
> The recovery tools in OS X would be nice.  But I don't really want to pay.  Could I use an external drive I've got my old windows stuff backed up on and possibly create a partition that uses an HFS+ filesystem?
I don't understand what you are asking. HFS+ is the filesystem that OS X uses, and what was likely "erased" from the drive. This means that the data is on the disc in the HFS+ format still. Most of the recovery tools out there can recover files from a FAT and not much else. (Some support linux filesystems). Unfortunately, without specific on Apple's HFS+ filesystem, recovery tools are a bit difficult to create.

I understand that you do not want to pay, I wouldn't either.

The best thing you could do for her is get an external hard drive and setup time machine so that you will have a backup in the future.

---

### Post by ghostslinger on 2008-08-14
My apologies on being unclear.  I really know nothing about filesystems and I only recently just got into Linux via Ubuntu so I'm really still learning quite a bit about computers in general (I wanted to be a network security admin originally, then I found out how unglamorous the job could be XD).
I have an external drive on me.  I don't know if I'm completely wrong here, but is it possible I could somehow create a partition on the external and configure it to be an hfs+ filesystem instead of a fat32 (which is what the windows backup is I believe).

Do forgive a clueless noob if I'm asking a question that is glaringly wrong.

---

### Post by cyberdork33 on 2008-08-14
> **ghostslinger said:**
> I have an external drive on me.  I don't know if I'm completely wrong here, but is it possible I could somehow create a partition on the external and configure it to be an hfs+ filesystem instead of a fat32 (which is what the windows backup is I believe).
Yes, I thought you were asking something more related to recovering the data... I think that gparted can create hfs+ partitions, and there is a livecd called "parted magic" that can also create hfs+.

---

### Post by aysiu on 2008-08-14
This screenshot tutorial I made should help you:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

It's designed for recovering files from Windows instead of Mac, so there are a couple important tweaks to the instructions:

1. You don't boot from CD through BIOS settings. You just hold down the C key while booting up the Macbook.

2. When selecting the filesystem of the drive to be recovered, select HFS+ instead of NTFS

---

### Post by cyberdork33 on 2008-08-14
photorec looks like what you are looking for...

---

### Post by ghostslinger on 2008-08-15
ok so photorec worked fairly well.
however, the external drive is a western digital with all the stuff salvaged on it.
but it won't autorun.  and I don't know how to get it to autorun for her since the first time it was used was with the live cd during recovery.  any ideas on what to do?  google hasn't done much for me.

---

### Post by aysiu on 2008-08-15
I'm not sure what you mean by "autorun." Can you explain that a bit more? All *photorec* does is recover deleted files.

---

### Post by ghostslinger on 2008-08-15
My apologies for being unclear.  Photorec worked (very well might I add :)), and it backed up the data onto a new western digital external hard drive.  The problem is, I'm not sure how to safely move the data back onto the internal hard drive.  Normally, the external hard drives I've used have an plug and play feature (what I refer to as "autorun") in terms of restoring files, and this time the external drive didn't have any software automatically start when it was plugged into the mac while in OS X.  I'm a noob through and through with this stuff, and I'm trying tobe careful in these final steps.  So my question is, how do I get the contents back into the internal drive?  Would I need to somehow create an image for restoration into OS X?

---

### Post by aysiu on 2008-08-15
Well, I think you have to reinstall OS X.

Once you do, plug in and open the external drive (it should show up as a drive on the desktop),  select the files you want to copy over, and then drag them to the desktop or Documents folder.

---

### Post by youfudoij on 2008-08-17
:guitar:it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.

---

### Post by youfudoij on 2008-08-17
:popcorn:it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.

---

