---
title: "Can Ping &amp; Lookup but no DNS in FireFox both"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by RetroDan on 2008-04-17
I have tried both the version 6 & 7 live discs.

I would like to continue onto a full ubuntu linux box but the non-working FireFox is a major obstacle .

I have read through some prior posts wthout finding a solution.
I have tried putting FireFox offline to try and clear DNS cache without success.

FireFox will work with numerical IPs but no DNS although other utilities DNS no problem

I am stumped. Any help would be greatly appreciated.

Should I just pack-it-in and go with something like Red-Hat?

Thanks for your time and consideration.

---

### Post by wormser on 2008-04-17
There is no need to pack it in.  It sounds like you have narrowed it down to a DNS issue.  Just set up [OpenDNS]("https://www.opendns.com/start/ubuntu.php") and you will be fine.

---

### Post by RetroDan on 2008-04-17
Thank you for the quick reply.

I will try what you propose however, I have already tried changing the DNS gateway to openDNS using the ubuntu network utilities. The ping and url lookup etc. works fine but for some reason the FireFox will not do a DNS lookup.

This is a very frustrating problem. 

Thanks again.

---

### Post by wormser on 2008-04-18
> **RetroDan said:**
> I have already tried changing the DNS gateway to openDNS using the ubuntu network utilities.

Try using their guide or put the OpenDNS settings into your router.

---

### Post by Pasty-Flawss on 2008-04-18
1. type into firefox about:config
2. filter "Ipv6"
3. Double click it too change the boolean to true.

Hope this helps :)

---

### Post by RetroDan on 2008-04-18
Thank you very, very much. That fix worked perfect.

I had heard mention that the IPv6 could be the problem but no suppled a way to shut it off.

Thank again. ISSUE SOLVD!

---

### Post by RetroDan on 2008-04-18
Thank you very, very much. That fix worked perfect.

I had heard mention that the IPv6 could be the problem but no suppled a way to shut it off.

Thank again. ISSUE SOLVD!

---

