---
title: "[SOLVED] dvd video"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-08
Hi

im trying to set my box up to play dvds. I was working from the info given [COLOR=Blue][here]("https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback")[/COLOR]

ive downloads and installed all of the codecs mentioned on these pages but when i run the command 
```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```i get the "command not found message"     the "examples" part looks like i should input something there? should i?

When i insert a dvd in to my dvd drive it shows on the desktop as a dvd icon and the title of the film.  Totem opens and displays  "an error occured.   Could not read from resource"

any ideas guys!?   :confused:

---

### Post by toupeiro on 2007-12-08
medibuntu has a good repo for dvd playback:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by discoade on 2007-12-08
Thanks!

That link got me just what i needed!

Many thanks


---

### Post by nikoPSK on 2007-12-08
darn I coul've helped, well since I'm here... I will:lolflag:

This is how to get it in totem:

here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. (if in gutsy replace the section of the top code 'fiesty" to "gutsy".

Hope that helps,
Niko

---

### Post by discoade on 2007-12-09
Nice one m8

i got my menus up now!  see its never too late!

Many thanks!  :guitar:

---

### Post by nikoPSK on 2007-12-09
glad to help.

---

