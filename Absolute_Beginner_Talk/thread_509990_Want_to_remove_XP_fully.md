---
title: "Want to remove XP fully?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-26
My experience with Ubuntu is very nice.I'm going to remove XP,couple of weeks later.Would you please tell me how should it be done safely?

---

### Post by G_force on 2007-07-26
you could use gparted to remove the windows xp install, bring ubuntu to front of the drive and resize that partion to takes up the remaining HDD space

---

### Post by RKCole on 2007-07-26
Hello, chatterjee.

Just make sure that any documents/photos/ersonal data is backed up to an external medium such as a CD-R or USB flash drive.

I had a friend whose Windows XP system became so infected taht ti wouldn't even boot.  Luckily, I was able to tell him by phone how ot use a Ubuntu Live CD.  We were able to get the data off of the Windows drive, and he then decided to do a full installation rather than hassle with the viruses any longer.

Do you happen to have any documents stored in the Microsoft Works format?  If so, there are some online services (free) that I've seen to convert the files to OpenOffice format among other formats.

In any case, once the Windows partition is cleared and it's formatted and has Ubuntu installed, you should be good to go.  Wahtever backups you make, you should just be able to copy them right over to your new Ubuntu system.

If I can be of any help, please let me know.

Good luck.

Take care.

---

### Post by OoooMatron on 2007-07-26
if you want to remove it safely take out the disc and smash it up with a hammer. That way you can be sure it won't return :D

---

### Post by ugm6hr on 2007-07-26
I would recommend the GParted LiveCD (just search google for gparted sourceforge) to delete the XP partition - careful that it's the right partition!!

Then just reformat the partition to ext3 (or fat32 if you prefer), and use it as storage/backup.  You could use GParted to make the Ubuntu partition bigger (as per G_Force suggestion), but I think having a spare partition is pretty useful for backups.

You could also convert the previous XP partition to /home - how to do that is in the psychocats tutorial (search for psychocats ubuntu).

Sorry about the search references, but I'm at work.

---

