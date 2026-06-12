---
title: "Silly servers question"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by SandersCraddock on 2006-12-12
This is probably going to sound stupid, but are you able to turn any computer into an ubuntu server?

---

### Post by taurus on 2006-12-12
Not sure what you mean by able to turn any computer into Ubuntu server?

---

### Post by SandersCraddock on 2006-12-12
Would i be able to run my regular desktop as a sever running Ubuntu server? Sorry Im a bit ambiguous sometimes.

Alex Craddock

---

### Post by taurus on 2006-12-12
Yes, you can install a server version and then install either Gnome, KDE, XFce4, or fluxbox with no problem at all!

```
sudo aptitude update
sudo aptitude install ubuntu-desktop  <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4
```

---

### Post by SandersCraddock on 2006-12-12
May give this a try on an old abandonned computer under my bed.

---

### Post by taurus on 2006-12-12
Depending on how much RAM that machine has, your best bet is go with XFce4 if it has less than 256MB of RAM...  Otherwise, both Gnome and KDE will be slow.

---

### Post by John.Michael.Kane on 2006-12-12
Have a read. 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

Theres also this.
[http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html)

---

