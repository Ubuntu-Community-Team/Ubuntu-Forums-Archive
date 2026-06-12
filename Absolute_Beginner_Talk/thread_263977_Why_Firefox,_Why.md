---
title: "Why Firefox, Why?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-24
I'm kind of new to Ubuntu, I switched from Windblows recently because there is nothing I can do to kill the virus I caught, and Windows just sucks anyways.  Anyways, about my internet.  I'm using Ethernet DSL, and Ubuntu recognized the conection.  The bad thing is, I can't go to hardly any sites.  The only search engine that works is Ask.com.  Many other pages might load, but only after an hour.  Also, some sites work just fine, like this one.  What else?  Firefox wont show pictures (like the ones you would see if you were searching in a search engines images).  How can this be fixed?!

---

### Post by jordanmthomas on 2006-09-24
Try this:
In the Address bar of Firefox, go to about:config
search for ipv6
Turn on ipv6
See if it works any better.

---

### Post by OptimusPrime on 2006-09-24
Thank you!

---

### Post by empcrono on 2006-09-24
> **OptimusPrime said:**
> Thank you!
 wierd... i woundeer how that stuff happens

---

### Post by LookTJ on 2006-09-24
> **OptimusPrime said:**
> Ipv6 is noware to be found.
not "Ipv6" only "ipv6"

in address bar

> about:config

in filter bar

> ipv6

set that to **true**

---

### Post by jordanmthomas on 2006-09-24
If you don't want to do anything *fun*, then ignore this post.
Personally, I have no need for ipv6, so I disable it from ever starting up (you would need to turn it back off in firefox)
```
gksu gedit /etc/modprobe.d/blacklist
```
At the end, add this line
```

blacklist ipv6

```
Works wonders in speeding up lots of internet stuff.  (though my networkmanager tells me 20 times that it is not loading ipv6 when I boot up, just an annoyance, not a real problem)

---

### Post by OptimusPrime on 2006-09-24
You are God, that fixed it all!

---

### Post by Ozitraveller on 2006-09-24
Enter IPV6 in the filter

---

### Post by OptimusPrime on 2006-09-24
> **Ozitraveller said:**
> Enter IPV6 in the filter

I found it, and it all works now.  Thank you all very much.

---

### Post by jordanmthomas on 2006-09-24
I think this thread is really really confusing.

---

