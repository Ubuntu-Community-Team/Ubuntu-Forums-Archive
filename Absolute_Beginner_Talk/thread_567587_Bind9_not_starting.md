---
title: "Bind9 not starting"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by ne0trace on 2007-10-04
Hello!
I wanted to test my newly set up DNS Server. Bit it seemed that my DNS Serverr is not running at all. So I tried to restart the daemon:

sudo /etc/init.d/bind9 restart

but the result is something like this:

 * Stopping domain name service... bind
rndc: connect failed: 127.0.0.1#953: connection refused
   ...fail!
 * Starting domain name service... bind
   ...fail!

And thats about it...

Any ideas?

Felix

---

### Post by ne0trace on 2007-10-05
I would be very happy if somebody could at least give me a hint where I could check a log file...

thank you
Felix

---

### Post by ne0trace on 2007-10-05
I can wait... :)

---

