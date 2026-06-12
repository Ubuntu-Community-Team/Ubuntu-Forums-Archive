---
title: "CUPS configuration under XFCE (XUbuntu)"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by uqbar on 2006-09-25
Hi all.
I've tried to configure a printer to be used with CUPS.
There is no XFCE setting for this and the web interface of the cupsd (127.0.0.1:631) refuses to let me in with my userid and password.
Any hint?

---

### Post by 5-HT on 2006-09-25
Admin access to the CUPS web interface has been disable by default.
To configure your printer from the web interface please refer to the following thread (ignore anything about w3m... you can use whichever browser you prefer): [http://ubuntuforums.org/showthread.php?t=195077](http://ubuntuforums.org/showthread.php?t=195077)

---

### Post by uqbar on 2006-09-25
Nope, it doesn't work.
I've tried logging into the cups web interface with root, cupsys and my own username with no success.
Only one account has a password set and it is mime.
Is there any other configuration front end as seen in Kubuntu?
Thanks.

---

### Post by bluefrog on 2006-09-25
you are sure you did the following?

sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

James

---

### Post by D10 on 2006-09-25
> **uqbar said:**
> Nope, it doesn't work.
Is there any other configuration front end as seen in Kubuntu?
Thanks.

I use xubuntu as well and have had spotty luck at best using the web admin for cups. I now just install gnome-cups-manager, and it has worked every time for me.

---

### Post by kboutin on 2006-09-26
Thanks for the trick D10 this worked for me with Xubuntu 6.0.6
on a THinkpad A21m and a Laserjet 1100 on lpt

---

### Post by SamChameleon on 2006-09-28
> **bluefrog said:**
> you are sure you did the following?

sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

James

I have tried it out and followed every step. It still does not work? Any suggestions?

This would be great, cause I would like to avoid installing gnome-print-manager :-k

---

### Post by maxpower on 2006-10-19
sudo aptitude install system-config-printer

works great for me

mAx

---

