---
title: "trouble with kaffeine"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by ktown on 2007-06-29
im going on a trip in less than an hour and was trying to play a movie with kaffeine and could not get it the work. are there an other alternatives to play dvd's on kubuntu.

---

### Post by Seisen on 2007-06-29
Did you install the dvd codecs or whatever their called?

---

### Post by ktown on 2007-06-29
no i didn't -- how do i get them?

---

### Post by Songwind on 2007-06-29
Install "xine-extracodecs" and "dvdnav" and you should be set for all your video playing needs.

---

### Post by Seisen on 2007-06-29
```
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install totem-xine
```

---

