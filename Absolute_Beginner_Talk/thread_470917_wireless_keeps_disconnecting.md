---
title: "wireless keeps disconnecting"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-06-11
hi

My wireless keeps disconnecting and it's never connected on start up. I have no idea why or how to fix it. iwconfig usually looks fine, but sometimes it says 0 link quality, signal level, and noise level. often it doesn't connect immediately when i use sudo /etc/init.d/networking restart.

any help with this would be much appreciated.

griff

---

### Post by Seisen on 2007-06-11
What is your wireless card?

---

### Post by Griffiss on 2007-06-11
asus WL-138G with Marvell W8300 chipset

---

### Post by Seisen on 2007-06-11
Have you tried using ndiswrapper to get it to work?

---

### Post by Griffiss on 2007-06-11
not since upgrading to feisty. but the card works some of the time (e.g. now) so the drivers must be working no? i don't really know how it works

---

### Post by Seisen on 2007-06-11
I had a dlink wireless card that would do that when I had dapper and then when I upgraded to edgy I had to use ndiswrapper to get it to work and it worked like a charm.

---

### Post by Griffiss on 2007-06-12
Yeah i did that with edgy too and it worked fine. would it need to be redone in feisty? i.e. would i have to uninstall and then reinstall ndiswrapper?

---

