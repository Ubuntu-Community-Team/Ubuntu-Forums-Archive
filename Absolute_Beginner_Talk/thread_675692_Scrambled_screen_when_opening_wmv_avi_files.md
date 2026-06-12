---
title: "Scrambled screen when opening wmv avi files"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by kugelblitz on 2008-01-22
When i open a media file I can hear sound from it but all I can see is a scrambled pink screen. Thumbnails will load up fine.

---

### Post by ajmorris on 2008-01-23
hi there,
have you tried installing libdvdcss (called libdvdcss2 in the repositories i believe) and w32codecs?

If not, install them via synaptic, or apt-get after adding the medibuntu repo to the bottom of /etc/apt/sources.list, and doing sudo apt-get update (or the re-load button in synaptic)
The easiest way to add this repository, is this (also does sudo apt-get update for you, if you use the commands i gave you):
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```(if you are not on gutsy, replace where it says gutsy, with your distro)

then do this to add the GPG code:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Also, if you have these already, but installed them via an application called AutomatiX, please uninstall them, and remove automatix, and then use the above method.
AutomatiX is not support by these forums, and is known to break systems.

---

### Post by bwtranch on 2008-01-23
Re #2

Good idea and then run

sudo apt-get update
sudo apt-get upgrade

Happy hunting:)

---

