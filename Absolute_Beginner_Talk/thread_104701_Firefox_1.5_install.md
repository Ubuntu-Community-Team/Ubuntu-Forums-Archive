---
title: "Firefox 1.5 install"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by tsarscott on 2005-12-16
I went ahead and tried to install Firefox 1.5 according to the wiki. I think I screwed up pretty bad :confused:  I am new to linux but, I figure the only way to learn anything is to jump in.
After the install, it wouldn't fire up. Tried from the terminal and here is what I get.
/opt/firefox/firefox.-bin: 
error while loading shared libraries: libstdc++.so.5:
cannot open shared object file: no such file or directory

Any help would be greatly appreciated.

---

### Post by bored2k on 2005-12-16
```
sudo apt-get install libstdc++5
```

---

### Post by arnieboy on 2005-12-16
[QUOTE=tsarscott]I went ahead and tried to install Firefox 1.5 according to the wiki. I think I screwed up pretty bad :confused:  I am new to linux but, I figure the only way to learn anything is to jump in.
After the install, it wouldn't fire up. Tried from the terminal and here is what I get.
/opt/firefox/firefox.-bin: 
error while loading shared libraries: libstdc++.so.5:
cannot open shared object file: no such file or directory

Any help would be greatly appreciated.[/QUOTE]
do
```
sudo apt-get install libstdc++5
```
and everything will be fine

---

### Post by tsarscott on 2005-12-16
Wow you guys are quick, thanks alot I'll be trying that in a few minutes.

---

### Post by tsarscott on 2005-12-16
:) Thanks it is working again. One of these days,  I might actually get the hang of Linux.

---

