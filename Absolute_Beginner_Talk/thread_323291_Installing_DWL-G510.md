---
title: "Installing DWL-G510"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by crum on 2006-12-21
Hi all,
I have just installed Ubuntu and I am haveing trouble installing my wireless card. I have checked out past posts on the site and try to follow what they have done and can't really get far at all. The standard thing that all the posts are saying firstly is what comes up for me is:
0000:02:00.0 Network controller: RaLink: Unknown device 0302
So I was wondering if anyone may point me in some direction on what to do first and so forth
Thankyou for everybodies time

---

### Post by ronybeck on 2007-01-07
Hi,

You really need to tell us a bit more other than  "It doesn't work.".  What I can suggest is that you do is go to the command line and type "ifconfig ra0 up" then type "iwconfig".  This will show us  what you have configured.  Be aware though that it will expose your wep key.

It would also be nice to know what you have done so far to configure the card.

With that info, we could help you a bit more.

Cheers,

Ronnie Beck

---

### Post by jjte on 2007-02-09
I had the same problem and ifconfig ra0 up wont help... one question when you go to System>Administration>Networking do you see wlan0 and wmaster0? if so then you probably have the dwl g510 rev.c, i spent hours trying to fix it only to realise that i had a rev c card.

you can get the drivers from here [http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com.tw/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

just compile and install, then you can use ifconfig ra0 up.

hope the drivers work for you.... i still cant get mine working, but i think thats ebcause of my dodgy router.

also you will need to configure the card after you install the drivers.

this is incomplete.... search rt61 edgy (or whatever version you are using) from the ubuntuforums home page

---

