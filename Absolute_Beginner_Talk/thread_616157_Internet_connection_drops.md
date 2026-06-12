---
title: "Internet connection drops"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-17
I'm on wireless internet and after about 10 minutes of use it disconnects for some reason? Any ideas why?

---

### Post by tyggna1 on 2007-11-17
Probably attempting a frequency change on your wireless card.   Check out
/var/log/kern.log 
and /var/log/syslog

those will point at a more certain reason.   Feel free to post them--if you can't make sense of it

---

