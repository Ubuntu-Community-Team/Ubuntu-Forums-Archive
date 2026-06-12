---
title: "using my brother's wpa protected wifi?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-12-31
hi,
this is probably an idiotic question.  i used compwiz's guide to getting wireless cards working, set up my home with wep, and everything is dandy.   i'm visiting my brother now and can't connect to his wireless which uses wpa.  how do i connect to this?  wifi-radar is no help and using the cli i get this:

sudo iwconfig eth1 essid KOALA
rich1@ubulinux:~$sudo iwconfig eth1 key s:{his password}
Error for wireless reques "Set Encode: (8B2A) :
     SET faile on device eth1 ; Invalid argument.

please help.
thanks,
rich

---

### Post by Sigudian on 2006-12-31
> **richieboy said:**
> hi,
this is probably an idiotic question.  i used compwiz's guide to getting wireless cards working, set up my home with wep, and everything is dandy.   i'm visiting my brother now and can't connect to his wireless which uses wpa.  how do i connect to this?  wifi-radar is no help and using the cli i get this:

sudo iwconfig eth1 essid KOALA
rich1@ubulinux:~$sudo iwconfig eth1 key s:{his password}
Error for wireless reques "Set Encode: (8B2A) :
     SET faile on device eth1 ; Invalid argument.

please help.
thanks,
rich

try to search the forum or the wiki.ubuntu.com for WPA and HOW-TO

---

### Post by shanepardue on 2006-12-31
I believe NetworkManager comes with WPA support out of the box. I know Knetworkmanager does at least.

---

### Post by wieman01 on 2007-01-01
Try the HOWTO in my signature if you have a minute. But NetworkManager is the right tool for mobile computers. You find it in the repositories.

---

### Post by Pobega on 2007-01-01
> **wieman01 said:**
> Try the HOWTO in my signature if you have a minute. But NetworkManager is the right tool for mobile computers. You find it in the repositories.

Just for archival purposes, [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

