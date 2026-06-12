---
title: "PowerMac G5 Airport Extreme Network Trouble"
date: 2007-02-22
forum: Apple PPC Users
---

### Post by randyjrsteffens on 2007-02-22
Hello, I am running Ubuntu 6.10 on my PowerMac G5. However, I am not able to connect to the internet via my airport extreme network. Any ideas on how I could correct this?

Thanks!

Randy

---

### Post by dnbkid on 2007-02-22
I don't know if it will work but as root try

modprobe airport

dhclient eth1

---

### Post by randyjrsteffens on 2007-02-25
Thanks for you suggestion.  It tells me "network is down".   Any other ideas?

Thanks!

--Randy

---

### Post by randyjrsteffens on 2007-02-25
Hi,

Update:  I am able to connect to the internet via direct ethernet, but still no success at getting any sort of wireless network connection via my airport extreme.   I've looked all over the message boards, and found some info that seemed like it may be applicable, but still no wireless connection success.  I have a bunch of other Macs on the wireless airport extreme network, so I know it *does* work.  Any Ideas?

Thanks!

Randy

---

### Post by Charpie on 2008-04-12
Trying to bring this issue back from the dead...

I've got the exact same problem. Just set up an Airport Extreme network and it works great on all my machines except my PowerMac G5 Dual 2GHz. The G5 says it's connected with full signal, but I've got a crap IP address, obviously one not assigned by the Airport. Everything worked great before I had an Extreme.

Anyone found a solution to this yet?

---

### Post by stream303 on 2008-04-12
I'm not experienced with wireless much - but from what I've read, it seems that Hardy - even in the current beta form, does much better with airport/express out of the box.

Although as usual, I could be wrong. :)

---

