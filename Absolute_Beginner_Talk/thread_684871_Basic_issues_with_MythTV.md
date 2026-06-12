---
title: "Basic issues with MythTV"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Terminal Sobriety on 2008-02-01
I CANNOT figure out how to get MythTV to find the media on my 500gb Seagate internal. I have a dual boot with XP on an 80gig. When I enter setup, u just cannot get it to come up with any media. Do i have to enter each folder (300+ music and 100+ video folders) individually? I put in /dev/sdb5/media/Media/Music/iTunes and it didnt find anything along with putting in individual folders and still no luck. Someone please hold my hand. This is discouraging the hell out of me and im sick of using M$.

---

### Post by emarkd on 2008-02-01
You don't want to point it to the device.  You want to point it to wherever that device is mounted.  Run 

```
mount
```

and see where /dev/sdb5 is mounted.

---

