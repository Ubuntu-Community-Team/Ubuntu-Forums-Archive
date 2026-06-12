---
title: "flash video problems"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-03-03
i cant play any videos from any sites really ebaums or utube it gives me a messed up videos window and never plays i have a fast connection and i think i have flash and gnome install anything i can do?

---

### Post by wolfen69 on 2008-03-03
in terminal:
```
sudo apt-get remove --purge flashplugin-nonfree
```
then download and install this one: [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb) just click to install. restart firefox if needed.

---

### Post by wolfen69 on 2008-03-03
also, for multimedia streaming in firefox to work correctly, do
```
sudo apt-get remove --purge totem-mozilla
```
then
```
sudo apt-get install mozilla-mplayer
```

---

### Post by ubuntu-freak on 2008-03-03
Follow my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and make sure you have everything you need, it will automatically skip anything you already have. There are also some useful settings you can use for the MPlayer browser plugin, other multimedia help and a troubleshooting section for any problems you may have.
 
Nathan

---

