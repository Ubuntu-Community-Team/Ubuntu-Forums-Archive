---
title: "Booting ubuntu from different driver files"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by slushpuppy on 2007-12-11
Hi, 
  I wonder if there is a way to boot ubuntu from different .xorg files as I am running ubuntu on external hardrives and have to switch computers from time to time,

---

### Post by Xbehave on 2007-12-11
i dont think so but you can specify multiple layouts and choose one using
              startx -- -layout <layout>
where <layout> names a section of your xorg.conf 
alternatively just have multiple xorg.confs and move them about
sudo mv xorg.conf.computer1 xorg.conf
or sudo mv xorg.conf.computer2 xorg.conf

---

