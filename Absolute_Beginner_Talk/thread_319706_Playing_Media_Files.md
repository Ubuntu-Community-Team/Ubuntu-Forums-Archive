---
title: "Playing Media Files"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by sameen on 2006-12-16
i have browsed alot in forums searching for the solution to my problem

i have 2 problem 

1)how can i play DAT & MP3 files in Drake Drapper

2)when i 1st installed ubuntu i didnot choose any  swap partition so i formatted that drive where ubuntu is installed & use mbrfix utility then i reinstalled ubuntu now 1 have noted that when it loads it takes more time in mounting the drive why is so ? same thing happens when i use live cd

---

### Post by bodhi.zazen on 2006-12-16
> **sameen said:**
> i have browsed alot in forums searching for the solution to my problem

i have 2 problem 

1)how can i play DAT & MP3 files in Drake Drapper

2)when i 1st installed ubuntu i didnot choose any  swap partition so i formatted that drive where ubuntu is installed & use mbrfix utility then i reinstalled ubuntu now 1 have noted that when it loads it takes more time in mounting the drive why is so ? same thing happens when i use live cd

For you mp3 issues look at this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

For assistance with swap post the output of ```
sudo fdisk -l
```And the contents of /etc/fstab

---

### Post by sameen on 2006-12-18
what about the DAT files ????

---

### Post by NeoLithium on 2006-12-18
I *BELIEVE* that mplayer can play dat files...check out their available codecs and information at [http://www.mplayerhq.hu](http://www.mplayerhq.hu)
Mplayer itself is available in the repositories, but I'm not sure if you might need an additional codec from their website. I'd just say install mplayer and try at first, if that fails, check their website.

---

### Post by xyz on 2006-12-18
How about....
[ How to play VCD .dat files using mplayer]("http://linuxhelp.blogspot.com/2005/10/how-to-play-vcd-dat-files-using.html")

---

