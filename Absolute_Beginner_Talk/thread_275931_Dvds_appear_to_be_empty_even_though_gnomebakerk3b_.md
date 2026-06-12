---
title: "Dvds appear to be empty even though gnomebaker/k3b message said complete burning..."
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by endorfin on 2006-10-12
I am trying to burn a dvd-r with gnomebaker and, even though that the burning completes just fine, when I try to read the dvd my laptop thinks it is blank. I have tried this with K3B as well and i got the same result. Anyone got any idea why this is happening?

About cds now, i prefer using k3b cause i found it more reliable than gnomebaker. With gnomebaker I used to face some problems unless i run it with (gk)sudo. Should i always run gnomebaker with sudo?

I am using ubuntu dapper.

Please help me. My hd is getting full, and I really need to burn these dvds.

Thanks in advance.

Edit: As far as the gksudo for gnomebaker is concerned, should I always use it? Both for cds and dvds?

---

### Post by ahaslam on 2006-10-17
Are you using the backports version (0.6.0)?
If so there's been a few problems, this should help:

**sudo chmod +s /usr/bin/gnomebaker**

Even if you're running a previous version it wont harm & will remove the need for gksudo ;)


Tony.

---

