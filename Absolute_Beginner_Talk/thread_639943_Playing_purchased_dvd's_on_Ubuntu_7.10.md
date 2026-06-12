---
title: "Playing purchased dvd's on Ubuntu 7.10"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-13
I'd like to play my dvd's on Ubuntu 7.10
My home movies will play fine but purchased
dvd's do not play.  I have installed VLC
but still a no go.... Could someone help me
out.

Thank you

---

### Post by stchman on 2007-12-13
> **Orbital75 said:**
> I'd like to play my dvd's on Ubuntu 7.10
My home movies will play fine but purchased
dvd's do not play.  I have installed VLC
but still a no go.... Could someone help me
out.

Thank you

You need CSS decryption.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

---

### Post by Orbital75 on 2007-12-13
Thank you.....  :KS

---

### Post by nikoPSK on 2007-12-13
well, rather than giving you a guide (though this is probably solved :)) I will point you through the steps to getting dvd in totem. This will enable menus and playback.

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

### Post by Orbital75 on 2007-12-14
Thanks.........  That will make this much easier. :KS

---

