---
title: "2007 24&quot; imac fails login with Nvidia driver"
date: 2016-10-18
forum: Apple Hardware Users
---

### Post by crimsonleech-gmail on 2016-10-18
This seems to be the Nvidia driver problem again, Nvidia-304 fails login with my GeForce 7600GT. Any way to get this to work, besides using the open source Nouveau driver?

This is using Ubuntu 16.10 64bit

Thanks for any help given.

---

### Post by crimsonleech-gmail on 2016-10-18
Looks like the Nvidia-304.132 is for linux 4.6 kernel and not 4.8, life and Nvidia sucks as usual

---

### Post by daftykins on 2016-10-30
Hi

Let me guess, X comes up but if you try to enter your password, it looks like it will load... but it actually kicks you back again?

First off, I think it would be a mistake to 'version-chase' by going for 16.10, I'd be inclined to pick 16.04 or in fact even 14.04, installing from 14.04.1 media so that you maintain the 3.13 kernel then dist-upgrade'ing afterwards (sudo apt update && sudo apt dist-upgrade) followed by installing nvidia-304 (or preferably newer) via your usual method.

Let me know how it goes!

---

