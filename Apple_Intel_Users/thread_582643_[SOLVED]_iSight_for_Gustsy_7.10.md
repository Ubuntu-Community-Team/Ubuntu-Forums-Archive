---
title: "[SOLVED] iSight for Gustsy 7.10"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by maluka on 2007-10-20
mine wasn't working right out the box. what's the best way to install it?

---

### Post by cyberdork33 on 2007-10-20
> **maluka said:**
> mine wasn't working right out the box. what's the best way to install it?

mine isn't either actually. It was at one time on the Gutsy pre-releases. What are you trying to use it with? Most people were reporting it as working in ekiga, but not in gstreamer.

---

### Post by [woodstock] on 2007-10-20
It works in ekiga indeed. I am currently trying to figure out how to make it work with gstreamer (and therefore mit most other programs as wegophone etc.)

---

### Post by cyberdork33 on 2007-10-20
> **'[woodstock] said:**
> It works in ekiga indeed. I am currently trying to figure out how to make it work with gstreamer (and therefore mit most other programs as wegophone etc.)
The issue with gstreamer 'should' be that it will not work at 640x480 even though it can. There is supposedly a fix in the latest gstreamer code that has not made it into ubuntu yet.

Try this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638/comments/40](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638/comments/40)

---

### Post by [woodstock] on 2007-10-21
Thank you for that hint. Unfortunately this causes "Cheese" to capture a picture only now and then while having a extreme heavy CPU load (which may be the cause of the lag). "Ekiga" isn't effected at all and "Wengophone" still doesn't work, so do "Camorama".

---

### Post by zmjjmz on 2007-10-21
The video finally works in Kopete
YAY!

---

