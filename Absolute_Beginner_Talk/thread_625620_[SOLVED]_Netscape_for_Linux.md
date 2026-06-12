---
title: "[SOLVED] Netscape for Linux"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-11-28
Ok I have netscape 9 loaded and running from terminal, how would I go about creating a launcher for it?

---

### Post by misfitpierce on 2007-11-28
Click desktop or bar and click add launcher and command is same as terminal. To add to menu if it did not auto do so just right click on menu part on bar and click edit menu.

---

### Post by J11Gyro on 2007-11-28
Thanks tried it got it :)  got tired of firefox crashing :(

---

### Post by ukripper on 2007-11-28
> **J11Gyro said:**
> Thanks tried it got it :)  got tired of firefox crashing :(

try iceape from fox family and it is in Gutsy repos, it looks like netscape and better supported than netscape in gutsy itself```
 sudo iceape-browser
```

---

### Post by J11Gyro on 2007-11-28
I am still running fiesty

---

### Post by ukripper on 2007-11-28
> **J11Gyro said:**
> I am still running fiesty

didn't realise before

---

### Post by atomkarinca on 2007-11-28
This can be a quick reference for you. In terminal browse into the directory you extracted Netscape (not the navigator directory) and type these:

```
sudo mv navigator/ /usr/local/
sudo ln -s /usr/local/navigator/navigator /usr/local/bin/navigator
sudo ln -s /usr/lib/mozilla/plugins/* /usr/local/navigator/plugins/
```

This way you get your Firefox plugins (e.g. flash, java...) installed for Netscape.

---

### Post by J11Gyro on 2007-11-30
Ok I have navigator 9.0.0.4 up and running by using a deb file I found on a link through the forums so it is installed as navigator.  I need some plugins so how do I install? Netscape can find no suitable plugins. Like flash or adobe reader

---

### Post by atomkarinca on 2007-11-30
If you have plugins installed for firefox then just type these in the terminal:

```
sudo ln -s /usr/lib/mozilla/plugins/* /usr/local/navigator/plugins/
```

---

