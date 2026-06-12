---
title: "Fingerprint Reader Support"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-28
I was wondering if there is any fingerprint reader support in ubuntu at all.  i just got a Toshiba  U205-S5034, and it has one.  Does anyone have any experience with this?

heres the laptop
[http://www.toshibadirect.com/td/b2c/pdet.to?seg=HHO&poid=352297&in_merch=1](http://www.toshibadirect.com/td/b2c/pdet.to?seg=HHO&poid=352297&in_merch=1)

---

### Post by moldy86 on 2007-03-01
i have a a135 series toshiba.. I tried everything i could find via google to get the finger print reader to work.. gave up.. 

but then it kept bugging me and found thinkfinger... Its made for ibms but works with sonys and toshibas. the site gives you everthing you need in the 2 documents on how to build it from source then install it which is very easy.. make sure to install mods into /etc/security. 
i had a little problem with the tf-tool. just move the lib its asking for to /usr/lib and all goes by great! any questions just pm me k

kevin kricfalusi

 :)

---

### Post by moldy86 on 2007-03-01
[http://thinkfinger.sourceforge.net/download.php](http://thinkfinger.sourceforge.net/download.php)

sorry go here for the source and docs

---

### Post by IcemanV9 on 2007-03-20
Depends on what kind of fingerprint reader device you have on your laptop.

In your terminal, type (to find out what kind):
```
lsusb
```

If it says "SGS Thomson Microelectronics Fingerprint Reader", then it might work on your laptop with [[COLOR="Orange"]**thinkfinger**[/COLOR]]("https://wiki.ubuntu.com/ThinkFinger?highlight=%28thinkfinger%29").

---

### Post by bigkahoona on 2007-03-23
The .deb installer works like a charm (on my ThinkPad T60, that is). I haven't actually seen much that works better straight away than the fingerprint reader. HOWEVER - it doesn't work with KDE login - yet. :(

---

### Post by Liakath on 2008-03-15
> **IcemanV9 said:**
> Depends on what kind of fingerprint reader device you have on your laptop.

In your terminal, type (to find out what kind):
```
lsusb
```

If it says "SGS Thomson Microelectronics Fingerprint Reader", then it might work on your laptop with [[COLOR="Orange"]**thinkfinger**[/COLOR]]("https://wiki.ubuntu.com/ThinkFinger?highlight=%28thinkfinger%29").


Thank you for the info provided.I have a Toshiba LAPTOP Satellite with the "SGS Thomson Microelectronics Fingerprint Reader". After following the guide given in the post I could get the same working. Thanks once again.

Liakath

---

