---
title: "Multi-touch - dragging with one finger while holding button with another?"
date: 2011-03-22
forum: Apple Hardware Users
---

### Post by dairyknight on 2011-03-22
I've just got the multi-touch driver work with ubuntu 10.10 64bit on my alumni macbook. Now I can do scroll and right click with two fingers.

However, one thing I really miss is the ability to move the cursor while holding the 'big button', say, I want to drag windows/icons with one finger holding down the physical button, and another finger dragging around.

Is there a way to achieve this?:confused:

---

### Post by matamoscas on 2011-03-22
I am in a similar boat.

I have faithfully and happily used Ubuntu on a custom built desktop for almost two years. I used it for about a year (at first) experimentally on my powerbook g4.

Well, six months ago, I got an intel MacBook Pro, and Ubuntu (because of the touchpad) has been virtually unusable.

It has improved, and I seem to actually be able to post without any of numerous unexpected things happening =) So, things have improved.

However, this behavior you seek, "hold down with thumb, and drag with a finger" does not exist.

So far I have found my experience with Ubuntu and a MBP to be poor, and that's putting it very nicely.  It is barely useable =( I am still waiting til I can use Ubuntu on my MBP =( =( =(


I guess, at least, as a consolation prize, Snow Leopard is a good OS.

---

### Post by dairyknight on 2011-03-22
Unfortunately Snow Leopar doesn't work very well if you're doing embedded development
and occadionally you need to build the kernel. :(


> **matamoscas said:**
> I am in a similar boat.

I have faithfully and happily used Ubuntu on a custom built desktop for almost two years. I used it for about a year (at first) experimentally on my powerbook g4.

Well, six months ago, I got an intel MacBook Pro, and Ubuntu (because of the touchpad) has been virtually unusable.

It has improved, and I seem to actually be able to post without any of numerous unexpected things happening =) So, things have improved.

However, this behavior you seek, "hold down with thumb, and drag with a finger" does not exist.

So far I have found my experience with Ubuntu and a MBP to be poor, and that's putting it very nicely.  It is barely useable =( I am still waiting til I can use Ubuntu on my MBP =( =( =(


I guess, at least, as a consolation prize, Snow Leopard is a good OS.

---

### Post by dairyknight on 2011-03-23
I just found holding & dragging works in the newest xf86 driver (see post above), though with a little bit sensitivity issue.

---

### Post by dairyknight on 2011-03-23
One problem I do discover about the new xf86 driver is that it seems not to with with touchegg. Touchegg needs 'evdev' while this driver uses multitouch. :(

---

