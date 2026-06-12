---
title: "partitioning"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by bass_baritone on 2006-01-28
i am running ubuntu (very happily) on my dell pentium 4.  i have yet to find any hardware that is unsupported... still getting acquainted, but i like her.  :)

...so i may have made some errors when i reformatted a partition for installation.  i think i corrupted/overwrote/whoknowswhat the partition with windows on it (no biggie - i backed everything up).  so what to do next...?  i still need windows (from what i read) in order to run photoshop.  so, i think i'm just going to start over and reformat that partition and reload windows and photoshop.  my questions are:  is this a good plan of action?  what should what format should i use for the windows partition (i read somewhere that linux formating of ntfs is problematic)?  or, would formatting the other partition for linux and running windows/photoshop with a simulator work better?

thanks for the advice

bryan

---

### Post by Bartender on 2006-01-28
Hiya bass -
Try this link out -

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

That's where I went for step-by-step directions.  Used the "Ubuntu + NTFS" directions, creating the FAT32 partition for sharing data.
If I read your post correctly you either don't have Windows anymore or can't access it?  Apparently you're better off doing a dual-boot with Windows installed first, so you may want to format the whole drive, get your Windows install up and running, then re-install Ubuntu.  When you install Windows you don't have to worry about doing any partitioning at that point.  I didn't.  Just let Windows have the whole thing, then partition it with the Ubuntu CD using GRUB and the directions on that website.
Whoopie, forgot one thing - I've read other posts where they recommended defragging Windows just before doing the dual-boot.

---

