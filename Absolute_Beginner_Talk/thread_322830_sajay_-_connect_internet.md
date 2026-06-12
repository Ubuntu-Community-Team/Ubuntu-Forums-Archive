---
title: "sajay - connect internet"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by sajay on 2006-12-21
I have a pctel internal modem.
its detected by ubuntu.
But i dont know how to activate it and use it.
how to dial to internet.?
i have a number,username,password given by my ISP provider.
dunno how to connect to the internet...](*,) .....

---

### Post by NeoLithium on 2006-12-21
This page should help you out :)

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by Plankman on 2006-12-21
Hi Sajay

The problem is probably your internal modem. Most internal modems don't work with linux, as they are winmodems and need a driver, etc. I'd suggest maybe trying to get hold of an external modem and see if that works.

Hope it helps

---

### Post by Canis familiaris on 2006-12-22
This is a known fact that internal modems do not work in Linux since they are Winmodems. However there is a project there called Linmodems.
Try visiting [Here (www.linmodems.org) ]("http://www.linmodems.org") and find your solution.

---

### Post by ieee488 on 2006-12-22
Personally, I like the using wvdialconf method the best. At least in the beggining to find where that internal modem is located. The reason I say this is because I have both Ubuntu 5.10 Breezy Badger and Ubuntu 6.06 Dapper Drake installed on the same PC. For 5.10, the modem is at ttyS14; for 6.06, the modem is at ttyS2. I would never had guessed ttyS14!!!

Of course, it goes without saying that the modem needs to be Linux-compatible for this method to work.

---

