---
title: "Dial up"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by teresa on 2006-05-24
I'm new to Ubuntu, Can anyone tell me how to hook-up to the internet without being logged in as Root?  When I try to log in as user, KPPP dials out and comes up no carrier.  If logged in as Root, the connection works fine.  Any suggestions. 
 Thanks

---

### Post by dmizer on 2006-05-24
according to this wiki ... [https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=DialupHowto](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=DialupHowto)

the problem is that you have to add your user to be a member of the dip and dial out groups.  so you need to add your username this way:
```
sudo adduser USERNAME dip
sudo adduser USERNAME dialout
```
substitute your username for "USERNAME".  then you should be able to dial out as you, and not as root.

---

