---
title: "Best Way To Wipe Everything?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-03-19
I've been using Ubuntu for a couple months, dual-booting with Windows. I haven't used Windows since day 1 once except to get some old files. I have a few permission problems, and I think I may have done some stuff I shouldn't have in the first week or so of using Ubuntu, and it's probably best if start fresh. I'm not a fan of grub anyway, I'd like the space, and I have a Windows computer if I need it. Anyway, so when Feisty comes out, I want to start new, having Ubuntu take up all the space my computer has. 

Now, I have 5 things that show up in GParted right now. ntfs, ext3, extended, linux-swap, and unknown. ntfs is Windows, ext3 is Linux. What do I need to do to get this to work? Can I just delete everything except ext3 in GParted, then boot from the CD and tell it to wipe my ext3 and install it from there? Will I be able to delete these "extended" and "linux-swap" partitions without any problems? Thanks.

---

### Post by teaker1s on 2007-03-19
If your sure that's what you'd like to do then deleting all partitions-when you reinstall you will be guided to repartition hard drive just like a new one:popcorn:

---

### Post by cam2009 on 2007-03-21
fantastic. but I just remembered my 2nd question, will doing this get rid of grub? thats probably a stupid question...but I guess I have no clue where it's stored.

---

### Post by confused57 on 2007-03-21
> **cam2009 said:**
> fantastic. but I just remembered my 2nd question, will doing this get rid of grub? thats probably a stupid question...but I guess I have no clue where it's stored.
You should be able to select something like "Use entire disk" for Ubuntu & it should over-write all your partitions currently on the hard drive, so you shouldn't need to manually delete your partitions before installing Ubuntu...grub willl be installed to the mbr, also overwriting the current grub.

---

### Post by Kabamaru on 2007-03-22
> **cam2009 said:**
> fantastic. but I just remembered my 2nd question, will doing this get rid of grub? thats probably a stupid question...but I guess I have no clue where it's stored.

Not an expert, but something to keep in mind:
If you only have one hard drive in your box, then grub will be there.  More than one hard drive and you'll have to find the first hard drive in line (in my limited experience, this has been the first hard drive that shows up on start up, while you're still able to enter bios - and not whatever drive you actually tell bios to boot first) and do a clean wipe there too.

---

