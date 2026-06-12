---
title: "[SOLVED] NX Client Wont connect"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by joshuanv28 on 2008-01-18
Ok i have been trying to connect to my Ubuntu Box through my windows Box but i keep getting the same message no matter how i configure NX.
Im new to using NX so I am not fimiliar with how exactly it works.
Im running  Windows XP, and Ubuntu server 7.10. Here is the Error message..
NX> 203 NXSSH running with pid: 2380
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 192.168.0.4 port 22: Connection refused

---

### Post by stump138 on 2008-01-18
You've installed SSH on the ubuntu computer correct?

If installed make sure that it is running on the ubuntu computer
```
ssh localhost
```

---

### Post by joshuanv28 on 2008-01-18
it said connect to host localhost port22:connection refused

---

### Post by stump138 on 2008-01-18
if you haven't already:
```
sudo apt-get install ssh
```
Then you can try:
```
ssh localhost
```
on your ubuntu machine.

If it is up and running you'll be prompted for a password then continue :)

---

### Post by joshuanv28 on 2008-01-18
I thought ssh was installed but i was wrong . it works great. Thx

---

