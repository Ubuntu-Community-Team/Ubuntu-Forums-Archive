---
title: "dvd playback"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-01-13
i would really like to play and watch dvds real badly and id like to use any video player

PS if i had S-vid out and i attach my t.v. to it how do i  i configure it to work on both screen and everything

---

### Post by nikoPSK on 2008-01-13
Try this:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. 

Regards,
nikoPSK

---

### Post by Kedster on 2008-01-13
ummm it kinda worked but this comes up now

ed but it says in encrypted
any way aroung this 



ill make a new post about the svid

---

### Post by Kedster on 2008-01-13
bump

---

### Post by Dr Small on 2008-01-13
Try VLC Player.

---

### Post by nikoPSK on 2008-01-13
> **Dr Small said:**
> Try VLC Player.

lol, ah well...;)

---

### Post by RomeReactor on 2008-01-13
> **Kedster said:**
> ummm it kinda worked but this comes up now

ed but it says in encrypted
any way aroung this

Hi. Try adding these packages:
```
sudo apt-get install libxine1-gnome libxine1-plugins libdvdplay0 libdvdnav4
```

---

### Post by Kedster on 2008-01-14
i got this lol i gotta go to school so be back at like 4 

```
kedster@kedster-lappy:~$ sudo apt-get install libxine1-gnome libxine1-plugins libdvdplay0 libdvdnav4
[sudo] password for kedster:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1-gnome is already the newest version.
libxine1-gnome set to manual installed.
libxine1-plugins is already the newest version.
E: Couldn't find package libdvdplay0
```

---

### Post by Circus-Killer on 2008-01-14
do the following two commands:

```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```

---

