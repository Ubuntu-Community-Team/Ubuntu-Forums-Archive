---
title: "I Broke My Kubuntu"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by BostonBrother on 2007-04-22
I just upgraded feisty on my hp laptop and got everything working.  My problem is that I went into the package manager to get rid of the bluetooth stuff because I don't have bluetooth on my machine and somehow ended up deleating many important files and applications to the point where my networking stuff doesn't work, kde doesn't work, just to name a few.  What I need to know is if I can re-install the lost applications without loosing my personal files which are all still there, (I'm still able to get into stuff using the recovery mode.)  Can I re-install using an install cd or something?

---

### Post by bobplano on 2007-04-22
can you get to the terminal? if you can you can just run (hopefully) sudo aptitude install kubuntu-destop and that will hopefully recover what you need

---

### Post by BostonBrother on 2007-04-22
I followed your suggestion.  I can still get into the terminal if I startup in recovery mode.  The problem is that I wiped out all of my network drivers and can't connect to the internet.  I can still run aptitude, but it can't download the files I need.  Is there a way to do the same thing from the alternate install cd?

BTW I don't know if this is important or not, but when I get into the terminal I don't need to use sudo I'm automatically logged in as root, even without entering in a password.

---

### Post by bobplano on 2007-04-22
i'm not sure if there is a 'repair install' feature but you can reinstall packages from the cd and one of the paskages should be the desktop enviroment. if you need ndiswrapper for the network drivers you can go to [packages.ubuntu.com]("packages.ubuntu.com") and copy the packages onto a usb stick (it should appear under /media) and then you can install what you need from the .deb packages so you can get your internet working again

---

### Post by zvacet on 2007-04-22
You can install from alternate CD with this (you don´t need sudo because in recovery mode you are root automaticly)

```
apt-cdrom add
```

```
aptitude install kubuntu-desktop
```

---

### Post by BostonBrother on 2007-04-22
I solved the problem for the most part.  I used the alternate install cd and chose the rescue option which got me access to my network card and then from a terminal window on my hard drive was able to use aptitude to install kubuntu-desktop.  So, everything is back with the exception of my wireless.  But that might be because I'm not quite sure how KnetworkManager operates.  Thanks for all your help though.  Live and learn, I won't make that mistake a second time!  :)

---

