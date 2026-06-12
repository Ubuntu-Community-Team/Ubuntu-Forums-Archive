---
title: "Can't connect to my network"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by kaveren on 2008-02-03
Hi

I have a problem.I can't connect to the other computers in my network when i'm using my wireless connection. It works fine when i'm using the cable.

When i'm connected with the wireless card i can connect to internet but not to my local computers. I can't even ping them, not the router either.

I've hope that someone can help me solve this.

Thanx!

---

### Post by spiderbatdad on 2008-02-03
interface eth1 (or whatever) not specified in smb.conf?

---

### Post by kaveren on 2008-02-03
I changed eth0 to eth1 and now it works :)
Thank you!

---

### Post by spiderbatdad on 2008-02-03
I believe you can set "bind interfaces only = False (or no) and you will be able to serve on either wired or wireless. Binding interfaces is considered a security feature, but I believe only insofar as if you had ppp modem configured. Another method might be to have interfaces = eth0, eth1...not 100% sure, but you get the idea.

---

