---
title: "Cron background process, ssh client, weird fault"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by jmknash on 2007-12-05
Hi

I can run this command manually fine, it connects with no error.

dbclient -R 10001:localhost:22 tunnel@192.168.10.10 -i /jffs/ssh/dropdss -y

--
But if I set to run automatically using cron it doesn't appear in top, there is no connection to
my server either....

Tested run as command in my server (using an http server admin 
which can run commands), output is:

dbclient: Warning: failed creating //.ssh: Read-only file system
Host '192.168.10.10' key accepted unconditionally.
(fingerprint md5 6a:9f:****:***)
dbclient: Failed reading termmodes


?????wtf

Jon

---

### Post by jmknash on 2007-12-05
Solved. Got it to run as background process without a TTY
dbclient -f -N -R 10001:localhost:22 tunnel@192.168.10.10 -i /jffs/ssh/dropdss -y

---

