---
title: "wireless adapter issue"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by frankc29 on 2007-05-10
As a complete noob I was quite proud of myself for getting my Dell Inspiron 1100 up and running as a XP/Feisty Fawn dual boot arrangement (I had to overcome an infamous and troublesome resolution issue, it was unbelievable frustrating! When I finally overcame the problem after many hours I felt I had accomplished some sort of quest). I then discovered that getting wireless adapters to work with linux in general very often presents a challenge. So after doing the requisite research I installed ndiswrapper via automatix 2 and used the System:Administration:Windows Wireless Drivers command to load up the latest XP drivers for my Linksys WUSB54GC. I thought it was a failure at first but soon discovered that it worked with one caveat. You have to boot up without the wireless adapter connected. Once the desktop appears and all hard drive activity ceases then I can attach the adapter, the green light flashes merrily, and I can configure the adapter, which shows up as "Wireless Connection" under Network Settings. There is a slight dip in connection speed, like 15%, over a Windows wireless connection with the same adapter over the same router but nothing serious, and I only notice it when running a internet speed test. Thing is, if you boot up with the adapter connected, or if you go into Hibernate or Suspend mode and then return, it doesn't work. No green light flashing. All of a sudden, in Network properties, rather than the single "Wireless Connection" I now see two additions, one called "Wireless Connection: Master" and "Wireless Connection: Lan0". But the adapter is dead. Is this the way I need to become accustomed to using my adapter or does anyone know of a fix? Maybe I should consider myself lucky that it works in such a predictable fashion at all? I have read some horror stories...

---

### Post by renzokuken on 2007-05-10
have alook here [http://marc.abramowitz.info/archives/2007/02/20/setting-up-a-linksys-wusb54gc-wlan-adapter-in-ubuntu/](http://marc.abramowitz.info/archives/2007/02/20/setting-up-a-linksys-wusb54gc-wlan-adapter-in-ubuntu/) and see if it helps at al

---

### Post by Austin_KW on 2007-05-10
yes, in that not an rt73 chipset.
Have a look at this howto for the native legacy drivers [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

