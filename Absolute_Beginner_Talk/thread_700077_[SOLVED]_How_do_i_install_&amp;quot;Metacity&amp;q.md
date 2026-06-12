---
title: "[SOLVED] How do i install &amp;quot;Metacity&amp;quot; and uninstall Emerald"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-02-18
someone help me out here plz thx...
just want to know how to un-install "Emerald" and need a guide or someone to tell me how to do this plz thank u ahead!

---

### Post by perlluver on 2008-02-18
```
sudo apt-get remove emerald
``` or you can just turn it off and turn on gtk-window-decorator --replace.  Press alt F2 and type that in the run box.

---

### Post by Bluestick on 2008-02-18
> **perlluver said:**
> ```
sudo apt-get remove emerald
``` or you can just turn it off and turn on gtk-window-decorator --replace.  Press alt F2 and type that in the run box.
sweet how do i install Metacity? can u help?

---

### Post by perlluver on 2008-02-18
Type in ```
sudo apt-get install metacity
``` although you should already have it.

```
metacity --replace
``` will turn it on.

---

### Post by Bluestick on 2008-02-18
> **perlluver said:**
> Type in ```
sudo apt-get install metacity
``` although you should already have it.

```
metacity --replace
``` will turn it on.

ok i did that

tom@tom-desktop:~$ sudo apt-get install metacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
metacity is already the newest version.
The following packages were automatically installed and are no longer required:
  lincity-ng-data librplay3 libsdl-gfx1.2-4 libqt4-core libqt4-gui
  libsdl-ttf2.0-0 rplay-client libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@tom-desktop:~$ 

But were is the program how do i get to it?

---

### Post by perlluver on 2008-02-18
Press Alt F2 and type in metacity --replace.  Then to change the theme go to system>preferences>appearance.  Other than that I don't know that you mean.

---

### Post by Bluestick on 2008-02-18
ok i got i see how it works, it doesn have like its own Metacity APP
its just build it ubuntu i got it thank you guys :)

---

### Post by perlluver on 2008-02-18
Your welcome, please mark as solved, in the thread tools.

---

