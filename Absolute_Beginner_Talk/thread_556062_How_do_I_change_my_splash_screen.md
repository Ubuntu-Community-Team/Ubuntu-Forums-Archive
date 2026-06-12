---
title: "How do I change my splash screen?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-20
Hi I looked at other posts using Configuration Editor to change the key in gnome-session,
I did all that and tried to point to my splash at ~/.gnome/splash.png
but it does not work:confused:

---

### Post by bodhi.zazen on 2007-09-20
Depends, what version of Ubuntu are you running ?

---

### Post by ROUBOS on 2007-09-20
Fiesty

---

### Post by defmer on 2007-09-20
also how do we do it in Gutsy?

---

### Post by st33med on 2007-09-20
[http:// http://web.telia.com/~u88005282/sum/index.html]("http:// http://web.telia.com/~u88005282/sum/index.html")
Good app.

---

### Post by Dr Small on 2007-09-20
I think you put too many http:// 's ;)

---

### Post by ROUBOS on 2007-09-21
Hmmmm no idea?

EDIT>>> GOT IT :)

placed the mysplash.png file I made into /usr/share/pixmaps/splash/     (with sudo)
then in gconf-editor and under apps>gnome-session>option changed the key to splash/mysplash.png

---

