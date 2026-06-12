---
title: "how to...5.10 to 6.06"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-06-11
hello all,

I want to finally make the change, but how do I make a clean install?  I read somewhere, but can't find it ,about GRUB problems.

I have 3 partitions.  1-WindowsXP, 1-FAT32 for sharing, 1-Ubuntu.

I want to just install it over the present Ubuntu.

Do I have to do anything special because I put the 6.06 in and it seemed to just start up the sytem as dapper as though it is a liveCD, but I am sure it is not.

the screen says start or install, but the install option never comes up.

do I have to delete the present Ubuntu partition?  if yes, how?

---

### Post by ed_d on 2006-06-11
From what I have seen, when dapper boots, after the "live" portion loads there is an icon to "install" just click that. From there just pick the present Ubuntu filesystm you want to over-write.

---

### Post by adam.tropics on 2006-06-11
I think you'll find it is a live cd! When the option screen comes up, just press enter and let it boot from the cd.
It will start Gnome, and on the desktop you will find an install launcher. Any data you have will be lost this way so backup first, and one piece of advice I have heard is not to do anything else with the system during the install. It's VERY fast so this shouldn't be too much of a problem, good luck!

---

### Post by JanVH on 2006-06-11
Upgrading the 5.10 to 6.06 distribution is easy and short.

First change every occurence of 'breezy' to 'dapper' in etc/apt/sources.list.
Then:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

Wait a little and everything is upgraded automatically.

---

### Post by PriceChild on 2006-06-11
or
```
sudo update-manager -d
```

---

