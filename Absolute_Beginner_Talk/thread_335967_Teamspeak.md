---
title: "Teamspeak"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by noenter1 on 2007-01-11
This is what keeps happening when i try to install teamspeak: 
```
no1enter@rurouni:~$ cd Desktop
no1enter@rurouni:~/Desktop$ tar -jxf ts2_client_rc2_2032.tar.bz2
no1enter@rurouni:~/Desktop$ cd ts2_client_rc2_2032
no1enter@rurouni:~/Desktop/ts2_client_rc2_2032$ sudo chmod 755 setup.sh
no1enter@rurouni:~/Desktop/ts2_client_rc2_2032$ sudo ./setup.sh
./setup.data/installer/installer: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```
I did go by the ubuntu wiki for it. [https://help.ubuntu.com/community/TeamSpeak](https://help.ubuntu.com/community/TeamSpeak) Anyone know how to fix this?

---

### Post by MkfIbK7a on 2007-01-11
looks like you are missing libX11.so.6...

---

### Post by noenter1 on 2007-01-11
Do you know where I can get it? Or do I need to reinstall something?

---

