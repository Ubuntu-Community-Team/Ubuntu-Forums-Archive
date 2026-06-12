---
title: "cant detect hard drive"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by glen122 on 2007-05-07
I have XP on one hard drive and Ubuntu on the 2nd HD. Either XP or Ubuntu will let me see old windows files that I had on the second hard drive (mp3's jpegs for example). I believe that when I installed Ubuntu, it saw these files for a few days, but has recently dropped them. Any help is most welcome.

---

### Post by Tundro Walker on 2007-05-07
[This post]("http://ubuntuforums.org/showthread.php?t=432695&highlight=fdisk+mount+hard+drive+fstab") should help you out.

About the 3rd poster down in it, **Cypher,** gives the right advice.  You want to...

```
sudo fdisk -l
```

...to see what /dev/??? your hard disks show up as.  Then, check your /etc/fstab file to see if they're included in there to auto-mount when booting.

---

