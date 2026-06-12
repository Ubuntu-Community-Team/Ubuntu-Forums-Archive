---
title: "Intel MacBook and Suspend"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by Alex&amp;Linux on 2008-03-15
Whats happening guys?
I put Ubuntu 7.10 on my Intel MacBook, and even though it eats through the battery charge at a higher rate, and there are always the requisite amount of random little problems, I'm still happy with it -however, Its a bit of a pain that I need to power the thing off in order to conserve the charge, and be able to use the thing!

To illustrate my point, I have an Excel sheet that I use to calculate long range ballistics.  When I have need for it, I'm in the middle of nowhere, so the battery is all I've got keeping my book running, but I have to maintain the program operational at a moments notice to input quickly changing data, it's not acceptable to turn it on and off.

So, I would like to be able to close the top, and have the thing go to sleep (with OS X, this was done, and power consumption was ~ 0, even after a few days of "sleep", this allowed me to go for a week or more on one charge. -I'd love to be able to do this with Linux!

What can we do about this?

---

### Post by cyberdork33 on 2008-03-16
Which Macbook version? What have you done to try and get it to work?

---

### Post by Alex&amp;Linux on 2008-03-17
Working with a 13'' intel macbook circa 2006, and what invariably happens is that when I try to wake it up from suspend, I get to the log-in screen, but only the keys on the right side of my keyboard will work, and the "num lock" light is stuck on (while it doesnt come on any other time!)

Quite the bug, I have tried to get around it by switching user, but the keyboard is just messed!

I heard that downgrading the kernel was a fix, but I'd be able to wait for an official resolution with my current version.

---

### Post by cyberdork33 on 2008-03-17
that doesn't sound like the issue that is fixed by downgrading the kernel... In fact, it sounds very strange indeed. If I had to guess, I would say that you have pommed installed, and it is not resuming properly after suspend for some reason... If you don't have pommed, then I don't know what your issue is.

---

### Post by nebhead on 2008-03-19
just to let you know i have the same macbook as you (late 2006ish) and i havn't had any of those problems, i would suggest you do a reinstall and use another ubuntu disc just to make sure your original install disc is not corrupted. if it happens again its a hardware issue and i am sure you can get help from people on the forum with more "know-how" than me. hope that helped.

---

### Post by Alex&amp;Linux on 2008-03-19
> **nebhead said:**
> just to let you know i have the same macbook as you (late 2006ish) and i havn't had any of those problems, i would suggest you do a reinstall and use another ubuntu disc just to make sure your original install disc is not corrupted. if it happens again its a hardware issue and i am sure you can get help from people on the forum with more "know-how" than me. hope that helped.

Thanks, I should have mentioned that I did a dist-upgrade from Feisty to Gutsy, could have had something to do with it.

I'll be heading off to reinstall right away!

---

### Post by cyberdork33 on 2008-03-19
doing an upgrade almost never works for me. Have to do a full install. Actually my home partition didn't make it from gutsy into hardy this time either.

---

