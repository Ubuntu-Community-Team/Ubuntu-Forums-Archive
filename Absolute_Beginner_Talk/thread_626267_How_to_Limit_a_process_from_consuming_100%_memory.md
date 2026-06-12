---
title: "How to Limit a process from consuming 100% memory"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by @ngkor on 2007-11-28
I am a new Ubuntu 7.10 user, I currently running WINE for some Windows applications (Longman Active Study Dictionary, DameWare NT Utility). Sometime WINE consumes up to 100% of my memory (RAM = 512MB), it stuck. 
I try to limited the memory used by a process to maximum 100MB in /etc/security/limits.conf by add a few line:
username hard stack 102400
username hard rss 102400
username hard memlock 102400
But this doesn't work.
Is there any other method to do this? or any Open Source Software has the same features as Longman Active Study Dictionary?

Thanks in advance!

---

### Post by staticvoid on 2007-11-29
maybe change its nice value in the task manager? this would be tempramental though....

sv

---

