---
title: "Update notice - file not authenticated - why?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-06-14
I received a notice that upgrades to my 7.04 installationi are available.  When I clicked to get the updates, I received a warning that the files are not authenticated.  Why would that be?  BTW, the files are XSCREENSAVER-DATA and XSCREENSAVER-GL.

I don't know what these files do, why I should get them or not get them.

Guidance would be appreciated.

Thanks.

Caruso

---

### Post by FuturePilot on 2007-06-14
Try ```
sudo apt-get update
```and see if it goes away.

---

### Post by Nythain on 2007-06-14
more than likely you are attempting to download them from a repository that you havent given a gpg key for... you can ignore the message as long as you trust where they are coming from

---

### Post by carusoswi on 2007-06-14
Udate is done - "finners" crossed.
Caruso

---

