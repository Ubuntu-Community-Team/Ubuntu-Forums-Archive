---
title: "screen resolution"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by jadda on 2006-12-22
Hi.
I installed ubuntu for the first time yesterday. It was the 5.10?? version. It didn't work so well so I updated it to the newest, 6,10 almost at once. It works very well, browsing is faster, I can watch and rip dvd movies, play mp3, and frankly it works pretty much "out of the box". But there is one thing. It gives me a headache. I can't set the resolution higher than 1024*768, the default resolution is 1200*800, or something like that. Can anybody help me?And another thing, can I turn of the touchpad?

---

### Post by shanepardue on 2006-12-22
What video card are you using? You may need to install a driver.

---

### Post by jadda on 2006-12-22
um...I'm feeling quite stupid here...but how do I find out?

---

### Post by shanepardue on 2006-12-22
System > Administration > Device Manager will show you all of your hardware.

Nvidia, ATI, and Intel make up for most video card manufacturers, but once we know what video 
card you have, we can go from there.

---

### Post by jadda on 2006-12-22
mobile 915GM\PM Express PCI Express Root Port
    NV43(GeForce Go 6600)

---

### Post by okipatrick on 2006-12-22
try some of the steps on the relevant part of this page
[http://lunapark6.com/?p=2501](http://lunapark6.com/?p=2501)

---

### Post by shanepardue on 2006-12-22
> **okipatrick said:**
> try some of the steps on the relevant part of this page
[http://lunapark6.com/?p=2501](http://lunapark6.com/?p=2501)
Please don't follow these steps unless you have an Nvidia video card. We need to know what video card you have first.

---

### Post by jadda on 2006-12-22
so,,,
should I do what okipatrick said?

---

### Post by macogw on 2006-12-22
Yes, shanepardue didn't see the post where you said what card you have.  It's an nVidia card.  Follow those directions.

---

### Post by jadda on 2006-12-22
I installed the driver and restarted my system, but I still can't set the resolution any higher, any suggestions?

---

### Post by shanepardue on 2006-12-22
Oh, I'm sorry. I did miss that post. type the following into a terminal and copy and paste the 
contents into a post on here so we can see what your configuration looks like.

```
gedit /etc/X11/xorg.conf
```

---

