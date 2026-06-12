---
title: "Wired Network Connection working with Windows, not with Linux"
date: 2012-09-27
forum: Any Other OS
---

### Post by Swanmate on 2012-09-27
Hi,

strange problem here, I'm pretty sure I'm missing something really stupid, so any hints appreciated with the following:

I'm connecting my PC to the internet via a router with DHCP activated - working in Win 7. Also, everything working just fine for any other device trying to connect to the internet, wireless and wired.

But for some reason, the DNS lookup keeps failing if I boot into Linux - with the configuration being exactly the same as in Windows (= pretty much everything set to "auto"), as far as I can tell.

---

### Post by Swanmate on 2012-09-27
And, as almost always, found the solution moments after posting this #-o.

The network manager wrote some funny stuff in my resolv.conf - manual edit did the trick.

---

### Post by Bucky Ball on 2012-09-27
Good news. Please mark as Solved from Thread Tools to help others.

Incidentally, are you actually using 9.10?

---

### Post by Swanmate on 2012-09-27
> **Bucky Ball said:**
> 
Incidentally, are you actually using 9.10?

Nope, Mint 13 (Ubuntu 12.04)

---

### Post by Iowan on 2012-09-27
Fixed that for you. I don't have versions available for Mint.
Not really Precise Pangolin, but closer than it was...

---

### Post by Perfect Storm on 2012-09-27
Moved to Other OS/Distro Talk.

---

