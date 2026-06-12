---
title: "sudo gedit vs gedit"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by faraazs on 2006-12-12
When I type sudo gedit <filename> the system asks me for my password and then idles after I enter it. gedit doesnt start...

However, when I type just gedit, gedit works fine... This seems to be only the case with gedit as I can still get temporary root permissions with sudo in other commands.

Any ideas on what is going on?

---

### Post by aysiu on 2006-12-12
What happens when you do this? ```
gksudo gedit
```

---

### Post by mcduck on 2006-12-12
try 'gksudo gedit'. You should always use gksudo instead of sudo for running graphical programs. (ok, most of the time sudo works too, but for some apps it doesn't and that can mess your system)

---

### Post by bulldog on 2006-12-12
You should use gksudo instead of sudo.

Why it won't work,beats me.

Edit:

LOL,enough reply's :-)

---

### Post by faraazs on 2006-12-12
Ah, didn't know about the gksudo thing. Thanks guys. I'll use that from now on.

However, that doesn't solve the problem. The window opens for gedit though but after that gedit freezes.

---

### Post by bodhi.zazen on 2006-12-12
> **bulldog said:**
> You should use gksudo instead of sudo.

Why it won't work,beats me.



[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

