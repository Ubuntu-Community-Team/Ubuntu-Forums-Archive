---
title: "Insanely Slow Internet"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by chichifelipe on 2008-03-21
Firefox has been taking forever to load, but it isn't Firefox.  Pinging my ISP gives me an average trip time of 670 ms (at 64 bytes).  In frustration I turned of my desktop and jumped onto my wife's XP laptop and pinged my ISP from there... average speed of 57 ms.  Now, where I live our "broadband" averages about 500kbps, but this is ridiculous and seems to be localized entirely to my Linux box.  Why is that computer's speed being throttled?  I'm running through an older Dell router and the laptop is running off a wifi connection from a linksys wifi point which is hooked to the same router.

Thanks

---

### Post by moephan on 2008-03-21
Have you disabled ipv6 in firefox? Usually a good pace to start. To do so, type "about:config" in the firefox location bar. In the filter box type "ipv6". Then, set disableIPv6 to "true". 

HTH

Cheers, Rick

---

### Post by hellomoto on 2008-03-21
I have just tryed what you surgested in your post... and it worked! Thankyou!

I am interested to know what IPv6 is and how come changing the setting to true made such a diffrence to the speed pages downloaded on firefox (I just kept timing out before).



I do have one other quick Q -- this is a minor prob. When ever I restart my comp i have to reload the drivers for my card in a terminal using:

sudo depmod -a
sudo modprobe ndiswrapper

is there a way to get the to happen automaticly when i restart?


thankyou again!

---

### Post by VyperX on 2008-03-21
go an tell your internet company (example: comcast, surewest)

---

### Post by IanW on 2008-03-21
> **hellomoto said:**
> 

I do have one other quick Q -- this is a minor prob. When ever I restart my comp i have to reload the drivers for my card in a terminal using:

sudo depmod -a
sudo modprobe ndiswrapper

is there a way to get the to happen automaticly when i restart?


thankyou again!

Add ndiswrapper to System/Preferences/Sessions in the Startup Programs tab

---

### Post by thiebaude on 2008-03-21
Moephan: My internet speeds are now much faster, thanks again.

---

### Post by asmoore82 on 2008-03-21
> **hellomoto said:**
> I am interested to know what IPv6 is and how come changing the setting to true made such
a diffrence to the speed pages downloaded on firefox (I just kept timing out before).

The current Internet as we know it is actually Internet Protocol version 4 or IPv4.
IPv4, some day, is to be replaced by IPv6 (version 6) or the so-called "Internet 2."
IPv6 will be necessary because it uses a longer address and can therefore support
more total connected machines; because of the somewhat inefficient way in which IP addresses
were handed out with version 4, we are set to run out of available addresses before too long.

IPv6 also includes many other advantages I'm sure but for now it's just an
**ultra** high speed backbone between Universities without much presence in "the real world."

[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

---

### Post by tuskenraider on 2008-03-23
> **thiebaude said:**
> Moephan: My internet speeds are now much faster, thanks again.

ditto!! totally fixed mine!!!

tusken

---

