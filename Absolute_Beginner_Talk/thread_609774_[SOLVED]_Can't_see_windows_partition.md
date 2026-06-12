---
title: "[SOLVED] Can't see windows partition"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2007-11-11
Hey. Seems like every time I get rid of a problem, a new one arises. It's fun, though, so I'm all right.

I've got a dual-boot Ubuntu-Vista machine. On Ubuntu, sometimes I can see my Windows partition, sometimes not. I've got no explanation, and no knowledge of this problem.

---

### Post by Pumalite on 2007-11-11
Have you checked in /media?

---

### Post by namanbagga on 2007-11-11
I have the answer to your problem.
If you hibernate vista or don't shut it down properly,ubuntu 7.10 will not detect the partitions

---

### Post by namanbagga on 2007-11-11
You can check out [my blog]("http://www.namanb.com") for more problems

---

### Post by DutyDuty on 2007-11-11
Now I have. Usually it appears either on my desktop or in my Computer folder. I ran ```
sudo ls -a
``` in media, just to be sure. It's not there.

---

### Post by DutyDuty on 2007-11-11
I'll try to boot windows and shut it down. See if it helps.

---

### Post by DutyDuty on 2007-11-11
Yeah, that did the trick. Just never touch Vista, easy enough.

---

