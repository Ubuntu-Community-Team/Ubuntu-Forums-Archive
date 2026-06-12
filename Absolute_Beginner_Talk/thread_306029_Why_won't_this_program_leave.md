---
title: "Why won't this program leave?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-24
I'm trying to get rid of Checkgmail. I did a "sudo apt-get remove checkgmail," and it seemed to work just fine. It asked me if I was sure if I wanted to remove it, and I hit "y" and it removed it...supposedly. I noticed that it was still in my tray, so I went into synaptic and made sure the package wasn't checked still, and it wasn't. What is going on? It is still checking for new mail every 120 seconds as if I never even did an uninstall.:confused:

---

### Post by saxin on 2006-11-24
Try to do a:
sudo apt-get remove --purge checkgmail

---

### Post by voodoonirvana on 2006-11-24
> **saxin said:**
> Try to do a:
sudo apt-get remove --purge checkgmail

I got this:


Package checkgmail is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



It's still in the tray, and working as if I never removed it.](*,)

---

### Post by bapoumba on 2006-11-24
Hi,
you may want to log out and log back into your session.
Not sure a **killall gnome-panel** will do it ;)

---

### Post by voodoonirvana on 2006-11-24
> **bapoumba said:**
> Hi,
you may want to log out and log back into your session.
Not sure a **killall gnome-panel** will do it ;)

That did it! Thanks.:)

---

### Post by bapoumba on 2006-11-24
Welcome :)

---

