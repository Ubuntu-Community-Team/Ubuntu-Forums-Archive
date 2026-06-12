---
title: "Installed Ubuntu over XP, now Vista wont boot! help!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Singee15 on 2007-08-29
Previously I had windows XP and Vista installed. I decided to delete XP and install Ubuntu (Feisty). So after grub installed it didn't have an option for booting to Vista. So i added one:
title Windows Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

but when I try to boot to it I get the dreaded "bootmgr missing" message. I have a lot of important info on the vista partition so I can't reformat or anything like that.

Any ideas?!

---

### Post by SOULRiDER on 2007-08-29
Ive never used vista so i cant help you there. Even if you have to reformat (which i highly doubt) you dont necesarily need to loose your data. Just mount the vista partition and backup allt he data. But im almost sure grub can be fixed...

---

### Post by nosrednaekim on 2007-08-29
thats probably because windows XP had the chainloaded windows bootloader, and when you wiped XP, you wiped the whole bootloader.

---

### Post by Singee15 on 2007-08-29
So is there a way to fix this without reinstalling? I don't have the vista disk :/

---

### Post by SpiritIsReality on 2007-08-29
howdy

til somebody shows up that knows, this is a good page to search
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+feisty+grub+vista&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+feisty+grub+vista&btnG=Google+Search&meta=)
[http://www.google.ca/search?num=50&hl=en&safe=off&q=site%3Aubuntu.com+linux+grub+vista&btnG=Search&meta=](http://www.google.ca/search?num=50&hl=en&safe=off&q=site%3Aubuntu.com+linux+grub+vista&btnG=Search&meta=)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuforums.org/showthread.php?p=3271133](http://ubuntuforums.org/showthread.php?p=3271133)

trails
edit:vlite to make a vista cd
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+vlite&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+vlite&btnG=Google+Search&meta=)

---

