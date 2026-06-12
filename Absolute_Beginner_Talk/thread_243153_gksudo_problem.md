---
title: "gksudo problem"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-24
Hi,
Im getting the following error when I try to run gksudo:

> 
gksudo gedit /etc/apt/sources.list
(gedit:8600): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Im trying to change the sources list so I can upgrade breezy to dapper.


Can anyone tell me whats wrong ?

Thanks in adavnce!

---

### Post by bulldog on 2006-08-24
There's nothing wrong.
Everybody get's that warning using gksudo with gedit I think.
I presume gedit is starting normal.

Nothing to worry about though.

---

### Post by aysiu on 2006-08-24
Read this, especially the bottom bit:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by bplus on 2006-08-24
unfortunately no gedit isn't starting.
Thanks for the info though.

I'll try with sudo (even though i shouldn't!)

---

