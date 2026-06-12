---
title: "What's this?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-29
I don't know but whenever i open something from terminal in something else i get this:

root@PCS-ADFR:/home/ubuntulinux# sudo gedit /etc/apt/sources.list

(gedit:4974): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Bachstelze on 2006-11-29
You should use **gksudo** instead of sudo.

---

### Post by rlozano on 2006-11-29
> **shoaibi said:**
> I don't know but whenever i open something from terminal in something else i get this:

root@PCS-ADFR:/home/ubuntulinux# sudo gedit /etc/apt/sources.list

(gedit:4974): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


you may want to try by pressing alt-f2 and typing gksudo gedit....

and try this if you still get the same error sudo nano /etc/.....

i think it has something to do with GUI, since gedit is a graphical interface and you are running that from the terminal. it should not be a problem though..

---

### Post by shoaibi on 2006-11-29
thanks problem solved, i tried gksudo

---

