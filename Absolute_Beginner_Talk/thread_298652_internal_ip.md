---
title: "internal ip"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-13
Hi everybody.
I'm trying to undestand how the pc connects with internet and ... all the stuff like that. So I was wondering how I can see which is my internal IP and if the setting of the connection to internet is made only thorough the browser.
I use  dapper drake.

Thanks for any hint.

---

### Post by nyinge on 2006-11-13
I'm not totally sure what you're trying to get here.  But...
```
ifconfig eth0
```
should give you your ip addr and other info, if you're connected with cable, i.e. not wirelessly.
```
netstat
```
should give you all the connections to and from your pc.  "netstat --help" will give you other useful stuff you might like to look into.

---

### Post by helphope on 2006-11-13
OK.
Thanks, it worked.
I'm trying to understand how the pc connects to internet.
Step by step

---

