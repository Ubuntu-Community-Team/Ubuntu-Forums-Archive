---
title: "how to play dvd"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by kinngg on 2008-01-14
i got problems running dvds on my gutsy, as soon as i insert the dvd my pc hangs and after that it just closes, anyone know any solution. I tried using vlc, mplayer and totem and all doesnt work

---

### Post by nikoPSK on 2008-01-14
to play them in totem here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. **(if in gutsy replace the section of the top code "fiesty" to "gutsy".)**

Best.
nikoPSK

---

