---
title: "getting internet properly set up"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by confudler on 2007-01-02
Hi I got running with Ubuntu 6.10 a couple of months back. One of the few problems (very quickly solved on this forum) was how to get the internet working. The solution was to go in to the terminal and "sudo dhclient". However, this has to be done every time I start up (which does not impress those I am telling that ubuntu is great and easy). Is there a way of correcting the actual startup configuration so that it is not necessary to run terminal every time I start up?

---

### Post by maxamillion on 2007-01-02
Technically you could make a small bash script that would run dhclient from /etc/init.d ... probably not the best of solutions, but it would work.

---

### Post by spockrock on 2007-01-02
now please dont try, this unless someone else confirms it but I believe if you, edit your rc.local(gksudo gedit /etc/init.d/rc.local) file and add to the bottom of the file

```
dhclient
```

and that might do it, I dunno, plx dont try that it might break ubuntu.

---

