---
title: "how to make kde applets works in gnome???"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by muzaki on 2006-03-09
hi guys, i just installed ubuntu breezy few days ago....
 
then i installed program ,this..
[[IMG]http://img102.imageshack.us/img102/2097/englishall4vk.png[/IMG]](http://imageshack.us)
[http://kprayertime.sourceforge.net/](http://kprayertime.sourceforge.net/)

**[SIZE="3"]KPrayertime Islamic Prayer Times Applet[/SIZE]**...so it`s working in my KDE environment because it`s an KDE (v3.x) applet....

**unluckily** I use gnome for my main activity, i dont like problems that occur when i use kde.....
so
**How** can i make this apps work in **GNOME???**
this is the list of installed file ...
> /.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/kprayertime
/usr/share/doc/kprayertime/copyright
/usr/share/doc/kprayertime/changelog.Debian.gz
/usr/share/doc/kprayertime-0.9.9.4
/usr/share/doc/kprayertime-0.9.9.4/AUTHORS
/usr/share/doc/kprayertime-0.9.9.4/NEWS.gz
/usr/share/doc/kprayertime-0.9.9.4/ChangeLog
/usr/share/doc/kprayertime-0.9.9.4/README
/usr/share/doc/kprayertime-0.9.9.4/TODO
/usr/share/doc/kprayertime-0.9.9.4/USAGE
/usr/share/doc/kprayertime-0.9.9.4/COPYING.gz
/usr/share/apps
/usr/share/apps/kicker
/usr/share/apps/kicker/applets
/usr/share/apps/kicker/applets/kprayertime.desktop
/usr/share/apps/kprayertime
/usr/share/apps/kprayertime/kpt.png
/usr/share/apps/kprayertime/kpt16.png
/usr/share/apps/kprayertime/latlong.dat
/usr/share/apps/kprayertime/madina.mp3
/usr/share/apps/kprayertime/madina_fajr.mp3
/usr/share/locale
/usr/share/locale/ar
/usr/share/locale/ar/LC_MESSAGES
/usr/share/locale/ar/LC_MESSAGES/kprayertime.mo
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/kprayertime.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/kprayertime.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/kprayertime.mo
/usr/lib
/usr/lib/libkprayertime.la
/usr/lib/libkprayertime.so


Please help me.....

---

### Post by chimera on 2006-03-10
pray for it to work:roll:

---

### Post by muzaki on 2006-03-10
[QUOTE=chimera]pray for it to work:roll:[/QUOTE]
LOL !!!:D :D  thanks..!!! any **better** solution ???

---

### Post by gord on 2006-03-10
im not too hot on my KDE stuff, but there is a gdesklet called prayertime which will give you praying times for whatever city you are in for the muslim faith... or somt like that :) 

just 
```
 sudo apt-get install gdesklets gdesklets-data 
```
and play about a bit :)

---

### Post by muzaki on 2006-03-10
thanks but i cant see the time number
[[IMG]http://img207.imageshack.us/img207/3566/screenshot0xx.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=screenshot0xx.jpg)

---

### Post by Perfect Storm on 2006-03-10
Strange, it looks like it's blurred somehow. Just tried it and it looks like this one mine.

[img]http://www.imageviper.com/displayimage/29221/0/prayer.jpg[/img]

---

### Post by muzaki on 2006-03-10
thanks and yeah i blurred that
and i can do like you said but whats the point? i cant see the time

Fajr: ?? -->> this should be number , not "??"

---

### Post by Perfect Storm on 2006-03-10
Ah, sorry. Just got distracted lol ^^

Check here: [http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=17](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=17)

or here: [http://www.arabeyes.org/project.php?proj=ITL](http://www.arabeyes.org/project.php?proj=ITL) you need to install two libs to get working.

---

### Post by Perfect Storm on 2006-03-10
itools, lib0 and libitl0 you can get if you have universe enable in your sourcelist:

```
sudo apt-get install itools libitl0
```

Then it should work.

---

### Post by muzaki on 2006-03-10
thanks solved:D

---

### Post by patrick295767 on 2006-03-10
Hi, 

Did you try kicker ?
 
```
apt-get -f -y install kicker
```
then, 
kicker &
  
You get the kde taskbar, and then u can play around with kde apps / applets ... 

Greetings

---

