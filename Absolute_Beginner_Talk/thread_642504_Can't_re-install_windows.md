---
title: "Can't re-install windows?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by BU5T4 on 2007-12-16
Hi  Guys,

I'm having some problems.

I have to re-install windows XP as I have some issues with ubuntu that I just can't seem to solve without more technical abilities that I lack unfortunately as Ubuntu runs great on my laptop.

I have tried to go back to windows by inserting my XP disk and booting up into the install. It gets so far then complains it can't find any hard drives. I thought it may be an issue with my windows CD and tried a friends but it does the exact same thing.

I had a scour through the forum and the only advice I could find was that I may need the manufacturers drivers for the sata drive. I have re-installed windows before after having ubuntu installed without needing such a driver.

I tried using the live cd with gparted to delete all the linux partitions and leaving just free space but the XP setup still doesn't detect the drive.

Am I missing something?:confused:

It would be great if I could have a dual boot of windows xp and ubuntu as I like using ubuntu but really need windows for things like my phone ( LG Viewty) and for using Svideo to play movies onto my LCD TV as it just doesn't work properly on ubuntu.

Any help would be greatly appreciated.

D-A

---

### Post by SunnyRabbiera on 2007-12-16
well before you do anything make sure to back things up as XP is a hog, it will want to eat up your whole HD as it has no decent partitioner or anything

---

### Post by Ub1476 on 2007-12-16
It IS because the XP disk lacks SATA/Raid drivers. Look [here]("http://www.community.probz.com/index.php?showtopic=1346") for more info.

---

### Post by BU5T4 on 2007-12-17
Hi,

Thanks for your advice.

I'll give this a try. I just don't understand why I would need to do this now when I havent had to do it in the past.

Odd.

Thanks

D-A

Note. Just checked out this site and it seems I need to have access to a windows install to run this software. You think I could use wine?

---

### Post by logos34 on 2007-12-17
> **BU5T4 said:**
> I have re-installed windows before after having ubuntu installed without needing such a driver.

If that's the case, then you may not need the sata driver.  I installed a seagate sata drive on a intel 915 board almost 3 years ago and labored under the illusion that I needed to put a sata driver on a floppy before loading xp home sp2.  But it turns out there was no driver needed, it runs in sata emulation mode using one of the ide drivers (atapi?) at (or very near) sata speed.

Maybe check the Bios settings.  Is it set for [auto]detect or user-specified settings?

---

### Post by SOULRiDER on 2007-12-17
> **BU5T4 said:**
> Hi,

Thanks for your advice.

I'll give this a try. I just don't understand why I would need to do this now when I havent had to do it in the past.

Odd.

Thanks

D-A

Note. Just checked out this site and it seems I need to have access to a windows install to run this software. You think I could use wine?

My friend had the same problem as you did, the program with the drivers didnt work on wine, we ahd to use a windows install.

---

