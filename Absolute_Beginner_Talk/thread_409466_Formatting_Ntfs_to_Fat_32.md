---
title: "Formatting Ntfs to Fat 32"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-04-14
First of all, I would like to thank every one for being so helpful the past few weeks. As what I am assuming is n all Volunteer group, I would have to say the customer Support Is so much more helpful than what Microsoft has. 

     My question is about formatting Hard Drives. Currently I am running with three hard drives. This has kinda made a mess of things. 

First Hard drive:         120 GB Window's
Second Hard Dive:     250 GB For storage. Pics, Music, and different files I do not want to lose in                                                         Windows.
Third Hard drive:         80 (But only recognizing 30) GB Ubuntu

The first and second Drives are written in NTFS, and I have yet to figure how to get Ubuntu to read from them. ( still a work in progress here) 

What I would like to do would be, using my Windows Resource CD, split my 120 Gig drive in half, and Make the half for windows NTFS. then divide my other 60 Gigs up for Ubuntu to install in.

I would also like to take my 250 Gb. Hard drive and format that to Fat 32 so both XP and Ubuntu could use the stuff on the drive.

What I do not have a clue is, Will an XP resource CD allow you to leave part of the Drive blank? or do I need to make it something? 

Can I change the format on a disk that doesn't have XP loaded to it?

what will I have come up asking which OS should be run? the Grub that came with edgy? or something from Microsoft? is there a better Grub out there? I tried to use Supper Grub but two out of three sites I could not get it to download from and the third site what I downloaded I could not get to work.

As always thanks for your help
Sabar

---

### Post by WiseElben on 2007-04-14
You can get Ubuntu to see and read/write from/to your NTFS partitions by installing ntfs-3g and ntfs-config. I think it's in the repos, so you can just:

```
sudo aptitude install ntfs-3g ntfs-config
```

As for resizing drives, you can just do it using gparted, which is also in the Ubuntu repos. You can leave things blank (ie, not formated) using this. I don't think gparted can save your data, but PartitionMagic (download the evaluation version), a Windows software, can do it.

Reinstalling Windows will override the bootloader. You will then have to place Grub as the default again. There are guides for doing this somewhere in the forums and Ubuntu Wiki.

---

### Post by Sabar on 2007-04-14
> You can get Ubuntu to see and read/write from/to your NTFS partitions by installing ntfs-3g and ntfs-config. I think it's in the repos, so you can just:

> sudo aptitude install ntfs-3g ntfs-config

So what exactly will this code do for me? do I need to make mounts and all that yet?

Sabar

---

### Post by N Clement on 2007-04-14
Gparted is a great utility.  I have repartitioned my 2 drives far too many times in the past few weeks, but it has done a great job.  It is capable of resizing partitions that have data on them without erasing.  Of course, it is a good idea to defragment a partition before resizing it and back it up if the data is really important to you.  I got an iso for a bootable CD that runs some stripped down form of linux with gparted as the only application.  When all else failed, my Gparted disc came through for me.

If you aren't familiar with disk partitioning, it wouldn't be a bad idea to post what your plan is first before you actually go through with it.

You can get the iso for the Gparted bootable CD [here.]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

---

### Post by GSF1200S on 2007-04-14
> **WiseElben said:**
> You can get Ubuntu to see and read/write from/to your NTFS partitions by installing ntfs-3g and ntfs-config. I think it's in the repos, so you can just:

```
sudo aptitude install ntfs-3g ntfs-config
```

As for resizing drives, you can just do it using gparted, which is also in the Ubuntu repos. You can leave things blank (ie, not formated) using this. I don't think gparted can save your data, but PartitionMagic (download the evaluation version), a Windows software, can do it.

Reinstalling Windows will override the bootloader. You will then have to place Grub as the default again. There are guides for doing this somewhere in the forums and Ubuntu Wiki.

Yeah.. I agree with this. NTFS3g allows Ubuntu to play the God OS.. Fat32 partitions like to fragment themselves bad.

Why limit yourself? The cool thing about NTFS3g is that you can have Linux save documents, music (anything really) on the NTFS partition and both Linux and Windows will be able to use it. I have NTFS3g up and running, and it hasnt giving me any issues...

Its really funny to create a text document, saved it to the windows desktop, and the next time you load windows, its sitting there like it appeared out of thin air :)

---

