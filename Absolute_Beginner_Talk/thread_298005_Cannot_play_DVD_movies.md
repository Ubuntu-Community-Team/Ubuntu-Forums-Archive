---
title: "Cannot play DVD movies"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by manas on 2006-11-12
Cannot play DVD even after runing command

sudo /usr/share/doc/libdvdread3/install-css.sh

any solution
My wife is gonna kill me Help me plssssssssssssss1](*,) :confused:

---

### Post by .t. on 2006-11-12
Add this to your sources.list:```
deb http://www.debian-multimedia.org sid main
deb-src http://www.debian-multimedia.org sid main
```

Then, "sudo aptitude update && sudo aptitude install libdvdcss2". It's only two steps away: and this way, if it ever gets updated, you'll have it in apt, so it can be.

Also, are you playing DVDs in totem-gstreamer (default) or totem-xine (better support)? Gstreamer support for DVD menus is poor, so if you want to use Totem, install totem-xine instead.

---

### Post by wehttamb on 2006-11-12
What happens if you try to play a dvd?

---

