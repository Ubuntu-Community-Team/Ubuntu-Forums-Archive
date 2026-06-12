---
title: "Feisty-Gutsy upgrade problem"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by ladede on 2007-12-03
When I upgrade my feisty to gutsy, my hsfmodem didn't work. So I download the newest hsf modem driver (something like 7.68....). But i cannot find it patch.. can nayone help me?

---

### Post by bumanie on 2007-12-03
Can't give any definitive answer about your modem, I can however tell you that there are many who have had to blacklist ipv6 to get the internet running on gutsy. It apparently does no harm at all to anything else, so it is worth a try.
In terminal type

gksudo gedit /etc/modprobe.d/blacklist

At the very bottom of the gedit list you need to type 

blacklist ipv6

Save the gedit file, restart your pc and all going well, your internet will work.

Although I returned to feisty, I have successfully got the internet working on gutsy via the above method. If in doubt, check this link
[http://www.lockergnome.com/linux/](http://www.lockergnome.com/linux/)
Scroll down until you find 'Ubuntu Gutsy Internet Help.'
Good luck.

---

### Post by laidback on 2007-12-03
I have ipv6 blacklisted all the time, read a recommendation about it in another thread.
Method as described above.

---

