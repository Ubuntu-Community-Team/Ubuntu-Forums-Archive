---
title: "[hardy] can't find the new update-notifier icon"
date: 2008-04-18
forum: Art &amp; Design
---

### Post by cast0r on 2008-04-18
hi,


Does anybody knows where the hardys new update-notifier icon is located?



... in hardy we have the  new update-notifier icon as seen below.
[IMG]http://img259.imageshack.us/img259/8617/screenshotqb7.png[/IMG]



the 
```
dpkg -L update-notifier | grep icons
```
 points me to the** /usr/share/icons/hicolor** folder, although the icons there are the old ones. :(

[[IMG]http://img134.imageshack.us/img134/8965/screenshotappsfilebrowsdi3.th.png[/IMG]](http://img134.imageshack.us/img134/8965/screenshotappsfilebrowsdi3.png)


Where can I find the new icons and which package provides it?


regards
castor

---

### Post by Half-Left on 2008-04-18
You can find it in.

/usr/share/icons/gnome/scalable/status/software-update-available.svg

---

### Post by smartboyathome on 2008-04-18
It is in the status folder of the GNOME icon theme, under "software update available". Next time you are searching for an icon, try looking for a keyword under the GNOME icon theme, gnome theme extra, human icon theme, and tangerine icon theme.

---

### Post by cast0r on 2008-04-18
thanks

---

