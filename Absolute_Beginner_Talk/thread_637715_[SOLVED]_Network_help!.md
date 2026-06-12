---
title: "[SOLVED] Network help!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by khurrum1990 on 2007-12-11
Hi, I have a speedtouch router. I can use it perfectly in Gutsy the problem is that in Fiesty while I was off line and I typed in speedtouch in my browser I would go to the router's home page to configure the router's settings and stuff. In Gutsy I can't do that any more. Can anyone help?

---

### Post by HermanAB on 2007-12-11
Type the IP address into your browser:
[http://w.x.y.z](http://w.x.y.z)

If you don't know what it is, look in the manual on the manufacturer's web site.

Cheers,

Herman

---

### Post by skymera on 2007-12-11
most likely 192.168.1.1

---

### Post by khurrum1990 on 2007-12-11
nope sorry it doesn't work. In fiesty I entered speedtouch.lan in the browser and the router's configuration tool opened.

---

### Post by khurrum1990 on 2007-12-13
I fixed it, all I need to type in is sudo dhclient eth0. That gives me the correct address and Ubuntu starts talking with the router.

---

