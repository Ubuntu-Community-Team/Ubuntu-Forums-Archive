---
title: "KDE in ubuntu"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Darkhorse13 on 2006-08-28
hi 

i'm a relatively new user of linux, and i read on the homepage that ubuntu uses gnome. i was wondering if KDE was also an option like in red hat versions, or whould i have to download kubutu?

Darkhorse13

---

### Post by Arisna on 2006-08-28
It is possible to do a base KDE installation with no frills in Ubuntu, but the usual way would be to install the kubuntu-desktop package using the following commands in a terminal:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

This will allow you to switch between GNOME and KDE if you wish without re-installing your operating system.

---

### Post by Darkhorse13 on 2006-08-28
cool man thanx allot!
 wow that was fast, usuallyit takes ages to answer any questions for ms products on other forums

cheers!
Darkhorse13

---

### Post by davebgimp on 2006-08-28
There's also XFCE

**sudo aptitude install xubuntu-desktop**

---

### Post by tralfaz on 2006-08-29
Last night I started this process with the commands below. I forgot about it in my hurry to go to work in the morning and by the time I remembered other family members had used the computer. I can't tell if it installed properly and I don't know how I would switch between the two.
(imac G3DV)
Any helpful hints?

> **Arisna said:**
> It is possible to do a base KDE installation with no frills in Ubuntu, but the usual way would be to install the kubuntu-desktop package using the following commands in a terminal:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

This will allow you to switch between GNOME and KDE if you wish without re-installing your operating system.

---

### Post by Jagot on 2006-08-29
When you log in at the GDM screen if you go into the options first there should be onee called 'select session' - if it install properly then KDE should be an option there.  If not, then just install again.

---

### Post by aysiu on 2006-08-29
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html) should help you.

---

### Post by tralfaz on 2006-08-30
Thank you! I hadn't noticed the options before. KDE wasn't there however, so I will try again.

---

