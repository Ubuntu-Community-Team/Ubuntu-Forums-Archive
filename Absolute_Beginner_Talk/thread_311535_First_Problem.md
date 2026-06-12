---
title: "First Problem"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by gazruss on 2006-12-03
Hi folks,
Re-installed Dapper today, had no probs with it so far, but i put in a new HDD and so decided to re-install. Everything went ok, did the software update, then rebooted. After entering my login and password i just got a black screen, with my mouse cursor. Hit ctrl, alt, f3 and got to the terminal. tried to use startx and got the following message:-

creating new authority file /home/garrie/.serverauth.4778
fatal server error
server is already running for display o
if this server is no longer running remove /tmp/x0-lock

Any idea's people.

---

### Post by ButteBlues on 2006-12-03
```
sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start
```


See if that works.

---

### Post by gazruss on 2006-12-03
it worked....

Thanx....

Now just need to find out why my network card won't work

---

