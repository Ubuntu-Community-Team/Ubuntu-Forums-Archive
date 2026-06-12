---
title: "Can't get Evolution or Thunderbird to connect to imap"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by squig on 2007-10-29
Recently upgraded to 7.10, and everything went fine. This evening I moved my home office to the other side of
the room. Suddenly, Firefox, Epiphany, and Evolution will not work. I did change from one phone outlet to the other, but the original one no longer works, so I think I can rule out primary/secondary line issues. I
can ping google, yahoo, etc., and I can access all Web sites with IE6
of IEs4linux, but can't resolve in the Firefox or Epiphany, and can't
connect to either of two imap servers using Evolution or Thunderbird.

I disabled ipv6 in Firefox and Epiphany, and they worked once more. So
I went looking for a global fix related to either ipv6 or DNS. I have
changed a couple of files, following the instructions from a couple of threads here... no deal. Anyone have any idea why my evolution accounts, which worked this afternoon, do not work now? They are both IMAP, one is google, the other is a small business I work for. Does it have to do with ipv6 or DNS or something else? Where can I look to find out? 

Many thanks for any assistance.

Humbly,
Squig

---

### Post by p_quarles on 2007-10-29
As I'm sure you'll agree, it's really bizarre that it just stopped working like that. Apart from that, there are ways to disable ipv6 systemwide, but I'll let you tell me what you've already tried before I hunt it down.

In any case, a stopgap fix would be to disable ipv6 in Thunderbird, which can be done the same way as in Firefox. Go to Edit >> Preferences >> Advanced, and click on the Config Editor. Search for 
```
network.dns.disableIPv6
```
and change its value to true.

---

### Post by squig on 2007-10-31
Thanks for the help with ipv6 in T-bird. It is now working. 

:)

---

