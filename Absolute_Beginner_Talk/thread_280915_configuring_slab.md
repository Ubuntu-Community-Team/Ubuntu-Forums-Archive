---
title: "configuring slab"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-10-20
how do i configure slab? particulary, i'm looking for how to keep it open after making a selection.

---

### Post by xyz on 2006-10-20
Would this help:
[http://ubuntuforums.org/showthread.php?t=215970](http://ubuntuforums.org/showthread.php?t=215970)

---

### Post by fuscia on 2006-10-20
that thread was more about installation, but thanks anyway.

here's the solution - 
open up gconf-editor and go to desktop -->gnome-->applications --> main-menu
and uncheck "urgent_close" at the bottom of the list of options.

---

### Post by xyz on 2006-10-20
> **fuscia said:**
> that thread was more about installation, but thanks anyway.

here's the solution - 
open up gconf-editor and go to desktop -->gnome-->applications --> main-menu
and uncheck "urgent_close" at the bottom of the list of options.
Great...thanks for letting me know.

---

### Post by gkasinath on 2006-10-28
> **xyz said:**
> Great...thanks for letting me know.

Hello all, 

This is my first post and I am ubuntu-ing for just over a month now. 

I came across the slab and quickly installed the gnome-main-menu from synaptic. 
Now, I noticed that the network status shows my wired connection (which I am never connected). And I hence wanted it to show my wireless connection. However, after reading the slab install/config discussion in Efty (now closed), I realized that I may need to rebuild the sources with my changes. 

However, when followed the guide in the forum mentioned above and apt-get install-ed the libs required (or so I may think). 
running ./autogen.sh gives me an error that I need to install gnome-common module. I was assuming that it was already installed, what am I doing wrong? 

Anyway, I have apt-get install-ed the gnome-common and related libs now.

Building the code, using ./autogen.sh now gives the attached error, please help!!

Uuumm, this is my first time building stuff on linux.

Thanks
Gautham

---

### Post by gkasinath on 2006-11-18
well, am still struggling with getting slab to show my wireless n/w status instead of the wired. Though this time its on Edgy. 

Hence the bump.

---

