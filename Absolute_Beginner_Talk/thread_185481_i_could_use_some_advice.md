---
title: "i could use some advice"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by cmt on 2006-05-31
hey, i want to make the switch from xp to ubuntu, I've got the cd to install, but I have a couple of questions...
1)I want to wipe xp off my laptop, my drive is ntfs, does it matter if its ntfs for a linux system, not sure what format i should put the drive in.
2)has anyone wiped xp and done an ubuntu install?  any words of advice?
thanks

---

### Post by macdo on 2006-05-31
You'll be asked during the install process how you want to reformat. You can't keep NTFS - that's an MS format. The normal choice is ext3. 
Just follow the installation steps, it's very easy...

Have fun - but remeber to back up that important data before you install!

---

### Post by rado_london on 2006-05-31
When installing ubuntu it will ask you to partition the drive. Delete the ntfs and create one ext3 and one small for swap around 500MB

---

### Post by user1397 on 2006-05-31
[quote=cmt]hey, i want to make the switch from xp to ubuntu, I've got the cd to install, but I have a couple of questions...
1)I want to wipe xp off my laptop, my drive is ntfs, does it matter if its ntfs for a linux system, not sure what format i should put the drive in.
2)has anyone wiped xp and done an ubuntu install?  any words of advice?
thanks[/quote] 
Couple of questions for you actually:  Which version of ubuntu are you installing?  I would suggest to wait for dapper, as it's only 30 minutes away.......

To install ubuntu, I would recommend the "ext 3" filesystem, it is the default one.  I would also recommend to make a root partition ( / ), a home partition ( /home ), and swap partition.  Tell me the size of your hard drive so that I can tell you how big you should make your partitions.  And yes, i've wiped xp from my computer trying to install ubuntu, but it was an accident.  Glad it happened tho, cause i like ubuntu far more than windows now!

EDIT:  Oh yea, and always remember to backup important data!

---

### Post by jodear on 2006-05-31
this is one of few threads I can answer . . . . during the install it will specifically ask you to erase XXX drive or erase and use XXX drive.  So erasing your NTFS partitions/drive will not be an issue.

---

### Post by gingermark on 2006-05-31
If you can back up any data you need then the installer has an option to wipe the disk and to install automatically, which is probably the easiest option.

If you have any experience in partioning, then I would advise creating a root partition of maybe 6 gigs, a swap partition of 2-3 times your RAM, and a separate home partition.

The home directory is where you keep your files and some settings, and by having it on a separate partition you can reinstall your OS easily without losing such data.

But if that's all gobbledegook just use the wipe disk option.

---

### Post by cmt on 2006-05-31
[QUOTE=erik1397]Couple of questions for you actually:  Which version of ubuntu are you installing?  I would suggest to wait for dapper, as it's only 30 minutes away.......

To install ubuntu, I would recommend the "ext 3" filesystem, it is the default one.  I would also recommend to make a root partition ( / ), a home partition ( /home ), and swap partition.  Tell me the size of your hard drive so that I can tell you how big you should make your partitions.  And yes, i've wiped xp from my computer trying to install ubuntu, but it was an accident.  Glad it happened tho, cause i like ubuntu far more than windows now!

EDIT:  Oh yea, and always remember to backup important data![/QUOTE]

thanks, i just (20 minutes ago) downloaded version 5.  I've got an 18gb hd on my laptop. whats the benefits of the different partitions?

---

### Post by gingermark on 2006-05-31
Use Dapper (Version 6.06). It's released today.

---

### Post by macdo on 2006-05-31
Having a root partition different from your home partition is good news if ever you need/want to reinstall. Because /home is where all your data and config files are, and because the new install will not overwrite them (as they're not on the same partition), it means that you don't have to reconfigure everything after installation. 

Don't let that stop you making backups, though...

---

### Post by cmt on 2006-05-31
Is there a link for 6.06, i run with that pony if its not a beta...
any cool programs to add?  basically i plan on using it for the web, email, and just learning how to use linux...its got a dvd drive so i'll probably watch movies.

---

### Post by Baasha on 2006-05-31
Erik,

Before you make the big leap you might want to read through the excellent instructions at:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This Illustrated Dual Boot Guide is full of good advice.  I have been running Win2K for quite a while and wanted to try Ubuntu out.  What I did, was go out and buy a new hard drive so I could keep the two systems completely separate.  You can also put Ubuntu on the same drive as long as you have enough room.

Ubuntu takes some getting used to, so to keep all my files accessible I opted for the dual boot system at least as long as it takes to get used to the Linux OS.  The Dual Boot Guide will tell you how to set up a FAT32 partition so you files will be accessible by both Windows and Linux.  That way if you decide later that you don't like Linux you won't have to go through the hassle of converting all your files back into Windows.

Just something to think about.

Bob

---

### Post by gingermark on 2006-05-31
Just wait a few hours for Dapper to be officially released.

And check out [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) once you have installed it to set it up to play DVDs etc. You'll also learn a lot doing that on how software is installed and other fun things.

There are lots of cool programs to add, but assuming you have a decent net connection I will leave it up to you to explore what is available - tis half the fun when you start!

---

### Post by Kilz on 2006-05-31
[QUOTE=cmt]hey, i want to make the switch from xp to ubuntu, I've got the cd to install, but I have a couple of questions...
1)I want to wipe xp off my laptop, my drive is ntfs, does it matter if its ntfs for a linux system, not sure what format i should put the drive in.
2)has anyone wiped xp and done an ubuntu install?  any words of advice?
thanks[/QUOTE]

Its nice that you want to make the switch. But are you 100% sure you want to remove windows off the bat? You can always remove it later if you set up a duel boot. Sometimes the switch can be harder than you think, leaving the windowz partition can smooth the transition.

---

### Post by cmt on 2006-05-31
i have to be honest, i'm not totally abandoning windows, i've got an xp tower, but i got the laptop from work, so i figured if i need windows, i can use the other computer.
i like that...spit a rat.

---

