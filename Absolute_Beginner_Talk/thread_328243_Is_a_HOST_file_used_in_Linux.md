---
title: "Is a HOST file used in Linux?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2006-12-30
I've used a HOST file for many years with Windows (this is my first day with Ubuntu). Can Linux use a HOST file to cut out advertisements and tracking sites like Doubleclick?

---

### Post by jonathan.lees on 2006-12-30
Yep the hosts file is used in Linux and is found in the /etc directory. It is used to look up the Internet Protocol address of a device connected to a computer network, such as your home computer connected to the Internet and not for cutting out adverts and tracking sites. You'd want to to use adaware or something similar for that.

---

### Post by TheWizzard on 2006-12-30
```
locate hosts | grep etc
```

---

### Post by Patrick K on 2006-12-30
> **jonathan.lees said:**
> Yep the hosts file is used in Linux and is found in the /etc directory. It is used to look up the Internet Protocol address of a device connected to a computer network, such as your home computer connected to the Internet and not for cutting out adverts and tracking sites. You'd want to to use adaware or something similar for that.

In Windows, I use it as a loopback as in these lines:
127.0.0.1  phpadsnew.abac.com
127.0.0.1  a.abnad.net
127.0.0.1  b.abnad.net
127.0.0.1  doubleclick.net

127.0.0.1 is the localhost. Your own computer. So when a website pulls an ad from or sends tracking info to a site on this list, no ad appears and no tracking info is sent, since it is redirected back to your own computer. In Windows, the system looks at the HOST file first to resolve the IP address. I'd guess it's the same in Linux but don't know this to be true. Try pinging 127.0.0.1.

In addition to this I have a small applet called Edexter that provides a small graphic place holder to keep the browser from waiting for the blocked ad site to respond. 

The downside is the HOST file can be very large and it can take some time to search it. Still, to me, worth it to foil advertising and tracking sites.

I actually didn't realize how much advertising there is on websites until running without these.

---

