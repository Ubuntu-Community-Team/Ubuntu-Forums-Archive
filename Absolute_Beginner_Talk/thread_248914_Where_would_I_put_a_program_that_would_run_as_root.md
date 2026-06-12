---
title: "Where would I put a program that would run as root?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Abstract on 2006-09-01
Hey,
  I've made a small bash program to mount a directory when I type a command via sudo. I put it in /usr/local/bin but then it gave me a command not found for sudo. Any hints on where to put it so root will find it in its path?

Also please note I do not want it mounted at startup so no need to suggest that ;).

---

### Post by Bachstelze on 2006-09-01
hmm /usr/sbin ?

---

### Post by taurus on 2006-09-01
Maybe /usr/local/bin is not in your path so you can move it to /bin then...

---

### Post by dmizer on 2006-09-01
first of all you'll have to make it executable:
sudo chmod u+x /usr/local/bin/scriptname.sh

then to run it, just use: sudo scriptname.sh
if it still says not found, then you may have to enter the fully qualified directory path:
sudo /usr/local/bin/scriptname.sh

---

### Post by Abstract on 2006-09-01
> **taurus said:**
> Maybe /usr/local/bin is not in your path so you can move it to /bin then...

This worked! Thank you. Also thanks to the two others who replied.

Wow this forum is quick.

---

### Post by taurus on 2006-09-01
> **Abstract said:**
> 
Wow this forum is quick.
Oh yeah...  ;)

---

### Post by etherstream on 2006-09-01
I'm pretty new to linux also, but wouldn't putting a program that runs as root in a publically accessable place be a security hazard?  A person could edit the script to execute arbitrary commands.

---

### Post by taurus on 2006-09-01
> **etherstream said:**
> I'm pretty new to linux also, but wouldn't putting a program that runs as root in a publically accessable place be a security hazard?  A person could edit the script to execute arbitrary commands.
If you set the permission right, nobody can read/write/run it except root...

```
sudo chmod 700 <filename>
```

---

### Post by Bachstelze on 2006-09-01
Do not confuse read/execute and edit. Users can read and execture stuff from /bin but only root can edit them.

---

### Post by etherstream on 2006-09-01
Ah, I was thinking that /bin had public write access.

Now that I think about it, having /bin with write access wouldn't make sense at all.

---

### Post by taurus on 2006-09-01
> **etherstream said:**
> Ah, I was thinking that /bin had public write access.

Now that I think about it, having /bin with write access wouldn't make sense at all.
You can make /bin writable for everybody but as long as the programs in there don't have the world writable permission, then nobody can edit those programs anyway...  But /bin should have permissions of 755.

---

### Post by Stone123 on 2006-09-01
Why make it simple when you can do it commpilcated.


sudo mkdir /root/bin

sudo echo "/root/bin" >> /etc/ld.so.conf && sudo ldconfig

sudo cp yourscupt.sh /root/bin

---

