---
title: "Stop me jumping out the window!"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by Revhead on 2005-08-02
For the love of God, can someone please explain to me step by step in words that even a child could understand how to mount and see my NTFS partitions on a SATA hard drive (VIA controller).
I have booted to the desk top using LiveCD, without incident.
I have even worked out how to mount the drives (I think) using the Terminal window and commands from the beginners guide (substituting sda# for hda#) - but they still do not appear in my computer. Just CDROM and FILESYSTEM?
This is driving me nuts. What the f**k am I doing wrong???

---

### Post by N'Jal on 2005-08-02
without access to my desktop i can't offer much more help than this, but try looking in file system, mnt, and see if your NTFS partition is there if not try looking in file system media, if it appears there (after you mount of course) there's a way to automount it on start up, but it's best to check if it mounts in the first place

---

### Post by bored2k on 2005-08-03
[QUOTE=Revhead]For the love of God, can someone please explain to me step by step in words that even a child could understand how to mount and see my NTFS partitions on a SATA hard drive (VIA controller).
I have booted to the desk top using LiveCD, without incident.
I have even worked out how to mount the drives (I think) using the Terminal window and commands from the beginners guide (substituting sda# for hda#) - but they still do not appear in my computer. Just CDROM and FILESYSTEM?
This is driving me nuts. What the f**k am I doing wrong???[/QUOTE]
 FRom a terminal run
sudo fdisk -l

Post it here, and tell us the drive you want mounted.

---

### Post by z3r0-c0d3r on 2005-08-03
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

---

### Post by Revhead on 2005-08-03
Thanks guys, especially Bored2K.
After doing some more reading I see you have responded to this same basic question so many times before.
I have been able to mount and access the drive.
My object in doing so was to perform an online virus scan and discover if I have a virus that is preventing XP from booting.
Finding an on line scanner that works with Firefox is not an easy thing I have discovered.
Of course I now realise even if I found a virus I would not be able to remove it because NTFS access is read only, right?
I think I'm just going to pull the plug on this one and reformat the partition, unless someone can offer some further advice.

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Revhead]Thanks guys, especially Bored2K.
After doing some more reading I see you have responded to this same basic question so many times before.
I have been able to mount and access the drive.
My object in doing so was to perform an online virus scan and discover if I have a virus that is preventing XP from booting.
Finding an on line scanner that works with Firefox is not an easy thing I have discovered.
Of course I now realise even if I found a virus I would not be able to remove it because NTFS access is read only, right?
I think I'm just going to pull the plug on this one and reformat the partition, unless someone can offer some further advice.[/QUOTE]

If you need the info, Partition Magic can convert from NTFS to Fat 32 without losing a thing.

---

### Post by Revhead on 2005-08-03
Good thought.
But if I could boot XP, I wouldn't need to install Partition Magic?

---

### Post by Mr. Electric Wizard on 2005-08-03
Not related to Ubuntu Linux...  sorry, but isn't there a pretty well known Knoppix hack for this?
There is a howto in the knoppix hacks book to do a xp off line virus scan.

---

