---
title: "sda1 - permission denied"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Jonzo on 2006-04-09
Does anyone know why I cannot access my Windows partition through Ubuntu? By default my Windows partition is sda1. So, it mounted /dev/sda1 in /media/sda1. Except, I always get "Permission Denied" when I try to enter it. Apparently 'root' is disabled by default on Ubuntu too, so I'm sorta stuck.

If i umount it, then re-mount it somewhere else - it does the same thing..

Any suggestions? Thanks

---

### Post by rado_london on 2006-04-09
well you can refer to [http://ubuntuguide.org/#automountntfs]("http://ubuntuguide.org/#automountntfs")
I used this method to get the nfts partition

Good luck

---

### Post by aysiu on 2006-04-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jonzo on 2006-04-09
Worked great, thank you!

---

