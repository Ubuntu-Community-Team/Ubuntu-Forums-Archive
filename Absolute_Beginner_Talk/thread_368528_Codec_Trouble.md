---
title: "Codec Trouble"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Merry on 2007-02-23
I've only just installed ubuntu 6.10 yesterday, and its my first foray into the world of Linux, so you'll have to forgive my stupidness.

I have two problems really, the first is trying to get Mp3s,WMAs etc to work through rhythmbox. I've tried using the w32codecs package and i'm not having any luck.

The second is that I would like to get my tv tuner card working (hauppuage wintv 848/849) it would appear that I have to download tvtime, however this is proving difficult as I cant use add/remove programs because the computer in question isnt connected to the internet, and, indeed cant be due to my universities ineptness/laziness/all of the above, all of which is making everything difficult!

---

### Post by taurus on 2007-02-23
Try this guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Merry on 2007-02-23
> **taurus said:**
> Try this guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

i have done!

---

### Post by igknighted on 2007-02-23
> **Merry said:**
> I've only just installed ubuntu 6.10 yesterday, and its my first foray into the world of Linux, so you'll have to forgive my stupidness.

I have two problems really, the first is trying to get Mp3s,WMAs etc to work through rhythmbox. I've tried using the w32codecs package and i'm not having any luck.

The second is that I would like to get my tv tuner card working (hauppuage wintv 848/849) it would appear that I have to download tvtime, however this is proving difficult as I cant use add/remove programs because the computer in question isnt connected to the internet, and, indeed cant be due to my universities ineptness/laziness/all of the above, all of which is making everything difficult!

I think rhythmbox is gstreamer based, so you need the package gstreamer-plugins-ugly as well (it doesn't hurt to get all those gstreamer-plugins available in synaptic however).

---

### Post by Merry on 2007-02-23
> **igknighted said:**
> I think rhythmbox is gstreamer based, so you need the package gstreamer-plugins-ugly as well (it doesn't hurt to get all those gstreamer-plugins available in synaptic however).

thanks, i've got it sorted.

I just need to sort the tvtuner out now!

---

