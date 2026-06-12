---
title: "Which do I choose?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by gd1984 on 2006-10-05
Hi, I have been using ubuntu 5.10 for a while and I am now going to download the new one (6.06.1) but I am I bit confused. 

You have three different kinds of the new one to download (Desktop CD, Server Install and Alternate install)

Which is the one I have to use to install it on the hard drive and have it boot up like an operating system each time I turn on my computer. Does the instalation work like the 5.10 one? 

Thank you

---

### Post by bigken on 2006-10-05
alernate is the text mode and desktop is the live cd which can also install 
go for the desktop cd ;)

---

### Post by xyz on 2006-10-05
Most people seem to recommend the Alternate CD.
The installation is simplified.

I was never able to install Dapper from any CD's...I had to install Breezy and than update/upgrade via the net.

Good luck! Let us know how it went...

---

### Post by PriceChild on 2006-10-05
Desktop cd requires 256Mb of RAM to boot up.

This lets you view a slower "live" version of the OS running off the disc, allowing you to install by clicking an icon on the desktop.

The alternate cd will install with barely any ram.

I prefer the alternate as i think its more stable... i would definately suggest it to you if you already know you're going to install.

---

### Post by Ben Sprinkle on 2006-10-05
Isn't there an option like:
```

sudo apt-get install dabber

```

---

### Post by PriceChild on 2006-10-05
> **Goat Spirit said:**
> Isn't there an option like:
```

sudo apt-get install dabber

```
Nope... but to upgrade on an existing install check out this: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Ben Sprinkle on 2006-10-05
> **PriceChild said:**
> Nope... but to upgrade on an existing install check out this: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

I thought there was an option to updrage to dabber through aptitude?

---

### Post by PriceChild on 2006-10-05
> **Goat Spirit said:**
> I thought there was an option to updrage to dabber through aptitude?
Read that guide, it is also possible to do it by changing all instances of breezy to dapper in your sources list then doing a dist-upgrade.

Please ensure to have ubuntu-desktop or kubuntu-desktop isntalled before doing so and prepare for breakage.

---

### Post by Ben Sprinkle on 2006-10-05
Ah yes, thanks.

---

### Post by deadgobby on 2006-10-05
Just a little heads up for you. You may need to reinstall your codecs after the upgrade. When I went from B to D. I had to reload the restricted codecs.

---

### Post by PriceChild on 2006-10-05
> **deadgobby said:**
> Just a little heads up for you. You may need to reinstall your codecs after the upgrade. When I went from B to D. I had to reload the restricted codecs.
Yup, because of the upgrade from gstreamer 0.8 to 0.10 for one.

---

