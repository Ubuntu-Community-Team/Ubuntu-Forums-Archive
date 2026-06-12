---
title: "problem installing realplayer"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by abdul on 2007-08-14
I have a problem installing realplayer, this is error what it shows.


rajath@rajath-desktop:~/Desktop$ sudo dpkg -i realplay_10.0.3-1_i386.deb (Reading database ... 77023 files and directories currently installed.)
Unpacking realplay (from realplay_10.0.3-1_i386.deb) ...
dpkg: error processing realplay_10.0.3-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package kdelibs-data
Errors were encountered while processing:
 realplay_10.0.3-1_i386.deb
rajath@rajath-desktop:~/Desktop$

---

### Post by aysiu on 2007-08-14
Try pasting these commands in the terminal: ```
sudo mv /usr/share/mimelnk/application/vnd.rn-realmedia.desktop /usr/share/mimelnk/application/vnd.rn-realmedia.desktop.old
sudo dpkg --configure -a
```

---

