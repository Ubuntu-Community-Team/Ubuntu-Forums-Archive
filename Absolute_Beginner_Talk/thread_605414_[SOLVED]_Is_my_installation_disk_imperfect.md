---
title: "[SOLVED] Is my installation disk imperfect?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by fulgencio on 2007-11-07
Hi, when I use my installation cd of ubuntu dapper drake it works just fine. but in the upper right corner of the screen an error mesage:

SIOCGIFFLAGS error: no device found

appears, if I install the system the problem persists. I use a HP Pavilion dv5000 AMD 64, I downloaded my cd 3 days ago. I have no idea if there is a relation but while loading ubuntu with the cd you can see:

RAID MONITORING SYSTEMS                                      [Failed]
I would like to know if this is normal or if this would make you think my downloaded disk is imperfect.
Please help I wouldn't like to download again.
thanks

---

### Post by dcstar on 2007-11-07
> **fulgencio said:**
> Hi, when I use my installation cd of ubuntu** dapper drake** it works just fine. but in the upper right corner of the screen an error mesage:

SIOCGIFFLAGS error: no device found

appears, if I install the system the problem persists. I use a HP Pavilion dv5000 AMD 64, I downloaded my cd 3 days ago. I have no idea if there is a relation but while loading ubuntu with the cd you can see:

RAID MONITORING SYSTEMS                                      [Failed]
I would like to know if this is normal or if this would make you think my downloaded disk is imperfect.
Please help I wouldn't like to download again.
thanks

Is there a good reason you are installing an Ubuntu version that is over a year out of date?

---

### Post by Sef on 2007-11-07
> Is there a good reason you are installing an Ubuntu version that is over a year out of date?

Dapper Drake is still valid until 2009 for the Desktop and 2011 for the server.

---

### Post by julian67 on 2007-11-07
The message is letting you know there is some hardware detected that doesn't have a suitable driver. It may be something to do with a RAID controller but on a laptop I'd guess it's more likely to be a wireless driver or firmware missing. These laptops variously use Broadcom, Atheros or Intel wireless and yours probably has the Broadcom. You can start here [https://help.ubuntu.com/community/WifiDocs]("https://help.ubuntu.com/community/WifiDocs")

---

