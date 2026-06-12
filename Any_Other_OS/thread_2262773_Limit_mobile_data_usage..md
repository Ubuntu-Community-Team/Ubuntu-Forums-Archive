---
title: "Limit mobile data usage."
date: 2015-01-27
forum: Any Other OS
---

### Post by PotatoHead007 on 2015-01-27
Hi.

I am a mobile data user, and i only have 3GB a month. Not much, but i make do.

I want to cap my daily data to 100mb per day, but i find no option to do this on my router menu(its a 3g router).
Is there a script or program i can use that sets a cap of 100mb per 24 hours?
Thanks.

---

### Post by PotatoHead007 on 2015-01-27
Looked around, still nothing...

---

### Post by Penguin360 on 2015-01-27
What does it have to do with Ubuntu?

P.S. I shouldn't have replied because we are using the same avatar, very confusing. LOL.

---

### Post by PotatoHead007 on 2015-01-29
Hi, haha :D

There must be a script or program that can do this?

---

### Post by Lars Noodén on 2015-01-29
I haven't used it but you might look at [tc](http://manpages.ubuntu.com/manpages/trusty/en/man8/tc.8.html) for [traffic control](http://tldp.org/HOWTO/Traffic-Control-HOWTO/intro.html).  I know it does rate limiting but it might also do more.  

About saving bandwidth, you could set up squid proxy/cache locally, if you have some disk space for a cache.  Then you can run your browser through it and repeat requests will get pulled from the cache instead of using your bandwidth.  Squid works out of the box with only HTTP but it can be tricked out to also do a MITM for your HTTPS traffic too.

---

