---
title: "winetools base setup problems"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-10
When I run the wine base set up I get thie

detecting Wine version... done.
Drive C: is /home/jim/.wine/drive_c
Wine 0.9.20
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.20".
Calls to wine are executed as  "wine".
Config is /home/jim/.wine/winetools.log.
Choice is Base setup
Choice is Create a Fake Windows drive with checked=F
waiting for wineservers to exit...

Then a message pops up saying it has run 10 second but that on slow computers this might necessarly mean any thing.  Then it says if you think your computer has hung you can kill it at the console by entering wineservers.  When I tried killing it that didn't do any good about every 5 second I get the same message.

What is going here? The computer I'm using is a Penitum 4 with a 3.0 ghz chip. So I wouldn't call that slow and I'm using a high speed dsl connection.

---

### Post by jbumgar on 2006-09-10
I'm sorry it is the winetools base setup.

---

### Post by jbumgar on 2006-09-11
Finally I figured out what was wrong with my install. By scrolling back up the terminal I saw it needed the GTK 1.2 installed.  Now it works fine.

How easy it is to over look the simple things.

---

