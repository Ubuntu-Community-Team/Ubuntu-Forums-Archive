---
title: "installing from .tar.gz files"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by shaheel16 on 2008-01-25
hi all.. well i have just installed ubuntu and i have downloaded the source files of vlc media player as a .tar.gz file.. I would like to know how to install it? well i tried the terminal with ./configure command.. after that the sudo make install command did not run.. dunno why.... anyone could help plz??

---

### Post by smurphy_it on 2008-01-25
Why are you installing VLC via ./configure and ./make commands and the like.  The program is already in the repositores.
Just type sudo apt-get install vlc

---

### Post by Jelmoh on 2008-01-25
It's easier to install via Synaptic, VLC is already in there so..
But if you want to use the terminal, use:
```
sudo apt-get install vlc -y
```
It installs VLC without asking if you really want to.. ;)

Good luck! :)

---

### Post by shaheel16 on 2008-01-25
thanks... i did it... btw the way what to do with files not in the directories that i have downloaded the source????

---

