---
title: "Can't Download Camra pics"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-03-11
Hi can someone tell me whats wrong here I just downloaded pictures last week using my 
Canon A530 Camera and now I can't.

[IMG]http://i19.tinypic.com/33f5c9v.png[/IMG]

Thanks 
Repent

---

### Post by HereInOz on 2007-03-11
I don't have the problem, but many do.  

You may find this post useful to provide a workaround until it all gets sorted.

[http://www.ubuntuforums.org/showthread.php?t=290205](http://www.ubuntuforums.org/showthread.php?t=290205)

Hope this helps.

---

### Post by Repent on 2007-03-11
But why would this just show up now?

---

### Post by FM1 on 2007-03-12
I think it was an update that broke imports from many cameras; the same thing happened with my S3 IS yesterday. All I did to get mine working again was change a line in /etc/udev/rules.d/45-libgphoto2.rules as described in the link below, then restart udev.

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

---

### Post by Repent on 2007-03-12
The 45-libgphoto2.rules file is read only how can I change it?

---

### Post by Repent on 2007-03-12
Bump

---

### Post by Repent on 2007-03-12
Please guys, I need to print some pictures for my sons science fair project .

---

### Post by compmodder26 on 2007-03-12
> **Repent said:**
> The 45-libgphoto2.rules file is read only how can I change it?

In a terminal, type: "gksudo gedit /etc/udev/rules.d/45-libgphoto2.rules" (without quotes)

That should do the trick.

---

### Post by Repent on 2007-03-12
Thank you that did the trick, :)

---

