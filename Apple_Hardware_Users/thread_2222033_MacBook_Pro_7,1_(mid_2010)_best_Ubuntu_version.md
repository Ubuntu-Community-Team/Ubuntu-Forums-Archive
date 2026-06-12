---
title: "MacBook Pro 7,1 (mid 2010) best Ubuntu version?"
date: 2014-05-04
forum: Apple Hardware Users
---

### Post by waulok2 on 2014-05-04
Hi.

I've tried a few versions of Ubuntu on my MacBook Pro mid-2010.
I currently have 12.10 installed but it appears WiFi is not going to work no matter what I do.
That is, WiFi can scan and see the networks around but for some reason cannot connect to my router.

The Wiki says:

> **[SIZE=2]Macbook Pro 7,1 and Ubuntu 13.04 (Raring Ringtail)[/SIZE]**

 This page describes the specific aspects of the installation of Ubuntu 13.04 on a [MacBookPro]("https://help.ubuntu.com/community/MacBookPro") 7,1. Note that this is seriously broken. My advice: install 12.04 instead.

Is this still the best version to use? 12.04? I don't see 12.04 on the wiki under MacBook Pro 7,1 anyway:

> 
[LIST]
[*]MacBookPro 7,1:
[LIST]
[*][Ubuntu 13.04 (Raring Ringtail)]("https://help.ubuntu.com/community/MacBookPro7-1/Raring") 
[*][Ubuntu 12.10 (Quantal Quetzal)]("https://help.ubuntu.com/community/MacBookPro7-1/Quantal") 
[*][Ubuntu 11.10 (Oneiric Ocelot)]("https://help.ubuntu.com/community/MacBookPro7-1/Oneiric") 
[*][Ubuntu 11.04 (Natty Narwhal)]("https://help.ubuntu.com/community/MacBookPro7-1/Natty") 
[*][Ubuntu 10.10 (Maverick Meerkat)]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick") 
[*][Ubuntu 10.04 (Lucid Lynx)]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid") 
[/LIST]
  
[/LIST]


Has anyone had any luck with any version of Ubuntu working 100% ?

---

### Post by Vinodh Moodley on 2014-05-05
I don't have the MacBook Pro 7,1. I have the 8,1 and I run Ubuntu 14.04 on it and it works perfectly fine. Maybe you should give 14.04 a try.

---

### Post by waulok2 on 2014-05-05
Thanks.
I managed to fix it by installing the latest Debian instead. WiFi works 100% straight away. Not sure why Ubuntu (old or new versions) failed to work.

---

### Post by Vinodh Moodley on 2014-05-06
Wifi was always a restricted driver for Ubuntu on my MacBook Pro. Once it's enabled, it works fine thereafter.

---

### Post by neoanderthal on 2014-05-06
Vinodh, does your MBP use the bcm wireless driver? My wireless is terrible; lots of dropped packets and timeouts. I've tried disabled the interface's power save and installed the restricted driver, but the problem persists. Everything else works well for me.

---

### Post by Vinodh Moodley on 2014-05-07
> **neoanderthal said:**
> Vinodh, does your MBP use the bcm wireless driver? My wireless is terrible; lots of dropped packets and timeouts. I've tried disabled the interface's power save and installed the restricted driver, but the problem persists. Everything else works well for me.

Here's a screenshot of the driver i'm using:

[[IMG]http://i1219.photobucket.com/albums/dd432/vmoodleyzaf/Screenshotfrom2014-05-07175403_zps8a0293cd.png~original[/IMG]](http://s1219.photobucket.com/user/vmoodleyzaf/media/Screenshotfrom2014-05-07175403_zps8a0293cd.png.html)

I think it's the same one you are using.

---

