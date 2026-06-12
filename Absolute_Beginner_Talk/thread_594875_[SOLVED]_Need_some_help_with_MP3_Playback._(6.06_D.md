---
title: "[SOLVED] Need some help with MP3 Playback. (6.06 Dapper)"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-10-28
totally lost on 6,06 dapper

---

### Post by Crafty Kisses on 2007-10-28
> **LiNuXxToOthEMaX said:**
> totally lost on 6,06 dapper
Install the package ```
gstreamer0.10-plugins-ugly
``` 

To add mp3 support to GnomeBaker, ```
install gstreamer0.8-mad
``` and ```
gstreamer0.8-misc
``` 

An alternative method to gain mp3 decoding support in gstreamer applications is to install gstreamer0.10-fluendo-mp3. This is in the  Universe repository, which contains software that is "more free" than that found in  Multiverse. More details on this plug-in can be found  on Fluendo's website.

---

### Post by LiNuXxToOthEMaX on 2007-10-28
> **Codename said:**
> Install the package ```
gstreamer0.10-plugins-ugly
``` 

To add mp3 support to GnomeBaker, ```
install gstreamer0.8-mad
``` and ```
gstreamer0.8-misc
``` 

An alternative method to gain mp3 decoding support in gstreamer applications is to install gstreamer0.10-fluendo-mp3. This is in the  Universe repository, which contains software that is "more free" than that found in  Multiverse. More details on this plug-in can be found  on Fluendo's website.

i did all that but the last one gstremer0.8-misc

it said something about package interrupted and then when I tried to reinstall it it said something to the extent of you have to reconfigure your packages

---

### Post by Crafty Kisses on 2007-10-28
> **LiNuXxToOthEMaX said:**
> i did all that but the last one gstremer0.8-misc

it said something about package interrupted and then when I tried to reinstall it it said something to the extent of you have to reconfigure your packages

If your package was interrupted, try the following:
```
sudo dpkg --a
```
That's worked for me in the past.

---

### Post by Crafty Kisses on 2007-10-28
Tell me if that worked.

---

### Post by LiNuXxToOthEMaX on 2007-10-28
> **Codename said:**
> If your package was interrupted, try the following:
```
sudo dpkg --a
```
That's worked for me in the past.

ya thanks!!!!

---

