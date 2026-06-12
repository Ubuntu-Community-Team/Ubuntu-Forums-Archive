---
title: "Activate Wireless Card on Boot Up"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by CATIII on 2008-04-07
Running 7.10 on a Dell Latitude D620 and finally got the wireless to work with it; however, every time I restart the computer the wifi light is off.  I have to enter the following to get wireless for that session:

sudo modprobe bcm43xx

So, I was wondering if there was a way to make the wireless card activate when the computer boots up?

Thanks

---

### Post by VMazza on 2008-04-07
My problem can potentially becomes like this one. I know little about computers so most of what I did was click and guess. I'm running 7.10 on a Dell Latitude D600 and FINALLY got a connection (which was amusing since I have a modem at home and shouldn't be a problem) AND made it to let me browse the web (click and guess 'solved' this problem.)

I have NO idea what's going to happen when I restart my computer. I don't really want to know. I'm just hoping it'll be on and working without having to go through the trouble of turning it on and praying it works.

---

### Post by bodhi.zazen on 2008-04-07
> **CATIII said:**
> Running 7.10 on a Dell Latitude D620 and finally got the wireless to work with it; however, every time I restart the computer the wifi light is off.  I have to enter the following to get wireless for that session:

sudo modprobe bcm43xx

So, I was wondering if there was a way to make the wireless card activate when the computer boots up?

Thanks

Add a single line to /etc/modules

> bcm43xx

---

### Post by CATIII on 2008-04-07
It worked! Thanks =)

---

