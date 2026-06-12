---
title: "rsync crash"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by illumeo on 2008-03-05
Hi
if i run rsync, on my server 7.10 after a while my system crashes, won't let me start a new terminal, all you can do is push reset. It is backing up a windows samba mount across a network. it has been working up to now. any ideas?

Thanks 

illumeo

---

### Post by hyper_ch on 2008-03-05
what happens if you run rsync in a screen terminal session?

---

### Post by illumeo on 2008-03-05
the same when i run it from the terminal (it is normally a cron job) i have not try to run it from a putty session but it think i would get the same result.

---

### Post by hyper_ch on 2008-03-05
what do the logs say?

---

### Post by illumeo on 2008-03-05
which logs should i look at (as i am running this from the cron as a command line and not a server service, i don't get an rsync log in /var/log/)

thanks

---

### Post by hyper_ch on 2008-03-05
maybe syslog

---

### Post by illumeo on 2008-03-08
this is the last line of the syslog before the crash


Mar  7 16:20:59 neuro kernel: [ 1553.554787] SMB connection re-established (-5)


any ideas?

---

