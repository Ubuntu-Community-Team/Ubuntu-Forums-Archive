---
title: "ddclient / dynamic dns help"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-05-07
Im tryin to get ddclient to report out to dyndns my ip when it changes. The problem is, the computer that the ddclient is on, is behind my router. 

So ddclient sends out my LOCAL ip (192.168.0.xxx) to dyndns. Is there a way to set it up so it sends out the routers IP instead?

---

### Post by dermotti on 2006-05-07
Well after googling, i found a solution that works. 

All you have to do is replace the following line in your /etc/ddclient.conf file :

[B]use=if , if=web
[/B]
With the following:

**use=web , web=dyndns**

Hope this info helps someone else!

---

### Post by Daiver on 2006-07-05
Thanks for this.  You saved me a long night of searching :)

---

### Post by splendid on 2006-08-28
Thanks this was a great help.  My IP can get updated, but for some reason ddclient service is not starting up.  Any ideas???

---

### Post by hellmet on 2006-10-13
^^same here.. any ideas?

---

### Post by Iarwain ben-adar on 2006-10-13
> **dermotti said:**
> Well after googling, i found a solution that works. 

All you have to do is replace the following line in your /etc/ddclient.conf file :

[B]use=if , if=web
[/B]
With the following:

**use=web , web=dyndns**

Hope this info helps someone else!

I love you :D

Thanks for the help man !


@ hellmet and splendid,
how do you mean, the service ain't starting?


Iarwain

---

### Post by hellmet on 2006-10-14
i've put 'ddclient' in the startup progs,
but for some strange reason, it doesn't start.
When I put 'gksudo ddclient' in startup, it asks me 
for password on startup and ddclient runs
successfully...
so, I'd want to start it as root...

---

### Post by Iarwain ben-adar on 2006-10-14
Hmm,
of that i don't know how to do.

If anybody knows,
please do tell :D


Iarwain

---

### Post by dermotti on 2006-10-14
Hmm, when i installed ddclient, it automagically put ddclient into my /etc/init.d directory, so it starts automatically that way.

---

