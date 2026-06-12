---
title: "Wireless interface and eth1 disappeared"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by taco_truck on 2006-12-30
I am very new to this whole linux ubuntu thing

When i installed ubuntu today, it did not detect my wireless card.

I was messing around with ndiswrapper and i did something and it now made the wireless interface icon and eth1 disappear from system>administration>networking.  Now i cant figure out how to get it back.  Would upgrading to version 6.10 restore it?  Some help is much appreciated.

I have a dell wireless 1370 wlan card.

Heres the link of the driver:  [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R140747&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=12&formatcnt=1&libid=5&fileid=187881](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R140747&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=8911&devlib=0&typecnt=1&vercnt=12&formatcnt=1&libid=5&fileid=187881)

When i type this in the terminal
```
lspci | grep Broadcom\ Corporation
```

I get this:

```
0000:03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I need some drastic help becuase i really need the wireless to work.  Thanx guys.  :D

---

### Post by sardion on 2006-12-30
Upgrading might help.

What did you do to ndiswrapper?

You could try reinstalling ndiswrapper...

Without more info about what caused the card to vanish I can't help much more.

---

### Post by taco_truck on 2006-12-30
Yea im downloading 6.10  hopefully that should restore my settings.  If not i guess i have to reinstall 6.06 or 6.10

I tried uninstalling ndiswrapper and still no luck,

When i do ifconfig or iwconfig it says eth1 no such device.  I really need to get the wireless working on here. I was trying about 5 HOWTO tutorials on the website and staying up till 2 in the morning trying to get the damn thing working.

Ubuntu recognized my friends card and he had no trouble gettting it working...

---

### Post by taco_truck on 2006-12-31
I uninstalled 6.06 and now i am downloading and installing version 6.10  hopefully that will fix the problem.

---

### Post by haiku99 on 2006-12-31
try this howto, worked for me w/ a similar card under Dapper and Edgy.....also follow the part about removing ndiswrapper first, if it is screwed up it is better so start over from scratch
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by taco_truck on 2006-12-31
Thanx for that.  I am downloading 6.10 as i write and going to install and partion and all that good stuff tonight.  Then ill mess around (hopefully get it workin) with that guide.  ;)

---

