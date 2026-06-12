---
title: "Real Player 10 Installation Error"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by batrachian on 2006-05-04
I followed Ubuntu FAQ Guide to install RealPlayer 10.  But after downloaded the file, I ran into this error while installing: 

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Does anybody know why?

Thanks in advance.

---

### Post by catlett on 2006-05-04
That means you don't have libstdc++.so.5 and real player can't run without it.
Using aptitude instead of apt-get can help sometimes. Instead of apt-get realplayer try ```
sudo aptitude install realplayer
```
I don't know the name of the realplayer file so I wrote realplayer for an example. Obviously write the correct name for it when you run aptitude install. Hopefully aptitude will install libstdc++.so.5 for you and then install realplayer.

---

### Post by batrachian on 2006-05-10
I tried and it is not working.  Any suggestions?

Thanks:eek:

---

### Post by Sutekh on 2006-05-10
Try having a read of [Ubuntu Wiki - Restricted Formats - RealPlayer](https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b)

---

