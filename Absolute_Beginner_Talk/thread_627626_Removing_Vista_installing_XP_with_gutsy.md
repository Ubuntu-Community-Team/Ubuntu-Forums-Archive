---
title: "Removing Vista installing XP with gutsy"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-30
I have an image of my hard drive that has three partitions Vista , Ubuntu , and swap I spent alot of time setting Gutsy and it is difficult to do it again .
I want to remove Vista by deleting its partition and install XP then restore  the Gutsy image.
THANKS

---

### Post by jken146 on 2007-11-30
All you need to do is install XP over your Vista installation.  The XP install CD will format the partition that has Vista on it and put XP there in its place.

After that, as XP likes to think it's the only operating system on your computer, you'll need to restore the GRUB bootloader so that you can choose to boot Ubuntu.  To do this see [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by ptn107 on 2007-11-30
For future reference you can store your /home folder on a separate partition so you don't have to lose your files and settings every time you reformat.

---

### Post by jmfa59 on 2007-11-30
jken146
I'll give a try.

ptn107
That's good you when making new installation with a copy of my recent home folder I can restore all the setting I made by replacing them.

---

