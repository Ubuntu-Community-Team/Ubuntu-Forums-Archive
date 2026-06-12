---
title: "Numlock [Resolved]"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by leckers on 2006-11-09
Please could someone explain how I obtain Numlock 'ON' after system boot. Ubuntu 6.10 just loaded for first experience of Ubuntu, and have managed to achieve Numlock on with other Linux distributions before. Am impressed with 6.10! Thanks.
leckers

---

### Post by aysiu on 2006-11-09
Turn numlock on and then paste these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://ubuntu.cs.utah.edu/ubuntu/pool/universe/n/numlockx/numlockx_1.1-5_i386.deb
sudo dpkg -i numlockx_1.1-5_i386.deb
``` That's the quick and dirty. If you want to understand a bit more about installing software, read these links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ecthelion on 2006-11-09
Install numlockx

[QUOTE=Synaptic Package Manager]numlockx:
enable NumLock in X11 sessions
Utilities to enable the keyboard's Numeric Lock during X11
session initialization.

Homepage:  [http://ktown.kde.org/~seli/numlockx/](http://ktown.kde.org/~seli/numlockx/)[/QUOTE]

---

### Post by jpeddicord on 2006-11-09
I *think* Edgy has the numlock bug fixed (default on), but make sure that you have installed all updates, and then restart your PC. Usually, if you have numlock turned on when you shut down, it should still be on upon startup.

Jacob

---

### Post by leckers on 2006-11-10
That's great! Works a treat. Wish I knew what I had done though - it's all pretty much 'magic' at the moment! Also, congratulations on the website - I will be doing some extensive reading there, as it appears to absolutley right for my low level of experience - thanks for that, too.
Ian

---

