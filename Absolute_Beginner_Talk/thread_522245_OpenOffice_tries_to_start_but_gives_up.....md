---
title: "OpenOffice tries to start but gives up...."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Mr lerame on 2007-08-10
I tried to start OpenOffice and it has an attempt then gives up without any errors displaying. On my travels around the forums I discovered that typing 'ooffice -writer' in a terminal will start it. Tried that and was rewarded with:  
  
~$ ooffice -writer
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: /usr/lib/libicule.so.36: cannot read file data: Invalid argument

** (process:8676): WARNING **: Unknown error forking main binary / abnormal early exit ...

I think it all started when I tried to install KDE on ubuntu from the kubuntu cd. I've been playing around with linux with a reckless disregard for other peoples hard work since I discovered ubuntu about 2 weeks ago......now I've wrecked it! (isn't this how we learn?)
Is there someone out there with a bigger brain than I've got, to get me back on track?

Thank you all.....

---

### Post by SOULRiDER on 2007-08-10
IMHO and experience, breaking things is the best way to learn. If i were you I would purge OOo and reinstall it, see how that goes.

To purge:
```
sudo aptitude purge openoffice.org
```

To reinstall
```
sudo aptitude install openoffice.org
```

---

### Post by Hagar Delest on 2007-08-10
First you can try to delete your OOo user profile (rm ~/.openoffice.org2). OOo will create a new one. If no improvement, you could try the official version instead of the Ubuntu version : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by Mr lerame on 2007-08-10
> **SOULRiDER said:**
> IMHO and experience, breaking things is the best way to learn. If i were you I would purge OOo and reinstall it, see how that goes.

To purge:
```
sudo aptitude purge openoffice.org
```

To reinstall
```
sudo aptitude install openoffice.org
```
Can I reinstall from the CD? I&#8216;ve only got a dial up modem and it seems pointless waiting for several hours while everything downloads again. I already tried adding the CD as a repository but it seems to be ignored. Could I be doing something wrong?......Oh YES!!!!

---

### Post by Mr lerame on 2007-08-11
Fixed it by booting from CD and replacing usr/lib/libicule.so.36 with uncorrupted copy. All seems well. 
What can I mess with next?.......

---

