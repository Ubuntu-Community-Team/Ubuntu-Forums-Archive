---
title: "Ubuntu 13.04 can't pair new Magic Trackpad"
date: 2013-06-09
forum: Apple Hardware Users
---

### Post by d4ni on 2013-06-09
I'm having issues pairing my Magic Trackpad.

The bluetooth menu detects it but when I try to pair it just fails, I try the automatic PIN, the 0000 PIN, everything. I've been searching and some people suggest using blueman-manager, which I tried and failed, also tried reinstalling bluez without success. Also tried a bizarre method I found about choosing 0000 PIN then automatic then 0000 again, without success.

Anyone out there had this problem or has an idea on what I'm doing wrong?

Thanks!

---

### Post by mihow on 2013-07-15
I had the same issue, but was able to get it to pair after choosing 0000 PIN then automatic then 0000 again, and then *repeating* the sequence until it worked. The bug is being tracked here:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/618838](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/618838)

---

### Post by mongole on 2013-10-09
Hi,

I read in the wiki article, that multitouch for left and right click is not working. Is this still valid in 13.04?

---

### Post by arthur3 on 2014-01-26
I managed to pair it in 13.04, several tries, more then 30. You have to make sure that 0000 is in place. In my case the conection of the trackpad was refreshing all the time and the automatic would kick in. 

Good luck!

---

