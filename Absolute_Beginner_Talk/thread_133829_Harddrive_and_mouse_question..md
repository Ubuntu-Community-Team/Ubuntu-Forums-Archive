---
title: "Harddrive and mouse question."
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by NLStone on 2006-02-20
Well I just started using ubuntu today, after the past couple of days looking around on various forums I found a lot of people recommend ubuntu.  I like it a lot so far and I've been doing a lot of reading but I have a couple of questions.

1.  My mouse is a Logitech MX700 and I was wondering if there is a quick and easy way to get all the extra buttons working.  Right now it's just the left, right and scroll work and I would very much like my thumb buttons back.

2.  I think I may know the answer to this next one but not sure.  I have XP on one harddrive, ubuntu on a another and then another much larger drive that I use for storage.  What I would like is for that drive to be usable whenever I'm in XP or ubuntu and I think I may have to reformat it to FAT32 so that ubuntu can read and write to it.

---

### Post by jimrz on 2006-02-20
Welcome,

1)  Take a look at this [[COLOR="Sienna"]**HOW TO**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=65471&highlight=mx700"). Seems to be what you are looking for.

2) If your large drive is ntfs you can read from ubuntu but not write (there are ways to do this, but they are risky and should be avoided). You could create a new FAT32 partition on this drive and use it to move stuff between os's OR, if you have PartitionMagic or similar utility, you could convert from ntfs to FAT32. I have done this successfully with Partition Magic, but it will only do it if the drive is, at least, less than 1/2 full since it needs room to work.

---

### Post by NLStone on 2006-02-20
Hey thanks for that bit about Partition Magic.  I bought it some time back and never used it and I didn't know it could do that.  Thanks again going to try it out now.

---

