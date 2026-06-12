---
title: "Trouble Setting Up GProFTPD"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by James_N on 2006-08-01
Hi

Im using the GUI of GProFTPD to try and set up an ftp server, but when i try to add users, i get this:

[[IMG]http://img527.imageshack.us/img527/857/screenshotbz1.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshotbz1.png)

But theres no uppercase letters in there or anything :confused: I dont understand why i cant create users? 

Thanks for any help :)

---

### Post by cstudent on 2006-08-01
Are you running gftdprod as root? 

From terminal:
```

gksudo gftpdprod

```

See if that will let you add the user. 


cstudent

---

### Post by James_N on 2006-08-02
thanks :) sorted that, but now when i try to connect, nothing happens. Ive forwarded port 21 in the router.

[ftp://81.108.208.162:21](ftp://81.108.208.162:21)

doesnt work :( Any advice on why?

Again thank you.

---

### Post by cstudent on 2006-08-02
You would definitely want to forward port 21 to your servers internal ip address. I'm not sure if Ubuntu is set up by default to block port 21, it may be. I use Firestarter on my machines. I have port 21 open through it for internal ip's and the only external ip I allow is from work. But that would be what I would check for. If port 21 is block at the server.

---

### Post by James_N on 2006-08-02
working now, so no worries :) thanks for your time.

---

### Post by cstudent on 2006-08-02
> **James_N said:**
> working now, so no worries :) thanks for your time.

My pleasure. :)

---

