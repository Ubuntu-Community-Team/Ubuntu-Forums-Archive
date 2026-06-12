---
title: "How to get USB as apt-get source"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by intangir1999 on 2006-10-20
I know that apt-cdrom lets me add a particular cd-rom to the repository (as far as I understand it), how can I do the same to a mounted USB flash drive?

---

### Post by TrendyDark on 2006-10-20
Are you trying to install .deb packages from the USB drive? If so, just browse to the USB drive and double click on the package you wish to install. Ubuntu Dapper and beyond have this wonderful application called GDebI (Graphical Debian Package Installer). It will install a .deb pacakage for you with no troubles and should also allow you to remove the program via Synaptic later on if you wish.

---

### Post by TheWizzard on 2006-10-20
if you just want to install a bunch of deb-files, you can just use: 
```
sudo dpkg -i *.deb 
```

---

