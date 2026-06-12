---
title: "[SOLVED] 13 in. 2009 Macbook (Wifi Issues)"
date: 2017-03-13
forum: Apple Hardware Users
---

### Post by anon24 on 2017-03-13
Ubuntu works great on this Macbook. The only thing that I have issues with is the wifi.

I tried to update and got this message:

```
~$ sudo apt-get update
[sudo] password for unknown: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```


TL;DR 
13 in. 2009 Macbook
Running Ubuntu 16.04.2 LTS

Connects via Ethernet, not wifi
Need help activating wifi card

Also, Terminal won't let me update
Need help getting Terminal to update OS properly

---

### Post by QIII on 2017-03-13
Moved to Apple Hardware Users for a better fit.

---

### Post by anon24 on 2017-03-19
SOLVED: For some reason, I had to delete all of my Network settings and re-enter it. I had entered it all during the install. Once, I did that, it works just fine.

---

