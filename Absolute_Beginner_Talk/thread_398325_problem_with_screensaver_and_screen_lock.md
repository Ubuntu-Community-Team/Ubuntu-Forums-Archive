---
title: "problem with screensaver and screen lock"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Lgndryhr on 2007-03-31
Hi.

I searched and searched until i came across this [thread]("http://www.ubuntuforums.org/showthread.php?t=288651&page=5"). I have not had a screensaver show up since I swtiched to edgy from dapper. I at first installed x-screensaver and did the trick to still use screen lock but I didn't like how the unlock screen looked so i uninstalled x-screensaver and undid
```
sudo ln -f /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command

``` by using
```
sudo rm ln -f /usr/bin/screensaver-command /usr/bin/gnome-screensaver-command

``` and also udid
```
 gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

``` by using
```
 gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver true
```

I also did the tutorial by getting the srouce og gnome power manager and editing it so i could see a screensaver. I had read this as a the best fix for this bug. Well i still cant see my screensaver I used in dapper and now can't lock my screen, TIA.

---

### Post by Lgndryhr on 2007-03-31
no one have any idea?

---

### Post by Lgndryhr on 2007-04-01
i fixed my screen lock problem. the command file was still there but not being directed correctly. now anyone know how to make my screensaver show up. i miss my matrix screensaver.

---

### Post by jpaint1021 on 2007-04-02
I'm having the same problem.  I set the screensaver I want, but when it should come on, the screen just goes black.

---

### Post by Lgndryhr on 2007-04-03
seems this a common problem all users of 6.10 are having with some screensavers. I can get some to show up but not some of the others I have.

---

