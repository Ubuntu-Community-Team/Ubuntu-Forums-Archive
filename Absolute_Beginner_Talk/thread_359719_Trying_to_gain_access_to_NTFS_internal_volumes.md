---
title: "Trying to gain access to NTFS internal volumes"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by tedrick on 2007-02-12
Hi, I have been advised to start a new thread because i am having trouble with ntfs-3g.  I was following the instructions when I got the following:

I am very new to Linux and Ubuntu, but from what I have seen so far it is great. However, in trying to set this facility up (NTFS configuration) after the first instruction I typed I got this message:

tedrick@FAMILYMAIN:~$ gksu gedit /etc/apt/sources.list

(gksu:6973): Pango-WARNING **: Error loading GPOS table 4097

(gksu:6973): Pango-WARNING **: Error loading GPOS table 4097

(gksu:6973): Pango-WARNING **: Error loading GPOS table 4097
(gedit:6974): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sys:1: PangoWarning: Error loading GPOS table 4097

What does it mean?

Thanks,

Tedrick

---

### Post by taurus on 2007-02-12
Try to use a text editor then.

```
sudo -Bw /etc/apt/sources.list
```

---

