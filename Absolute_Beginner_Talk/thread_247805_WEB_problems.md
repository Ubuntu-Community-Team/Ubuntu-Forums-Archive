---
title: "WEB problems"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by dimitryp on 2006-08-31
I have DSL router with **DHCP** server and Laptop with XP.
It works **fine** with XP and **Kubuntu** - but not works with **Ubuntu** :evil:

(kubuntu and ubuntu = liveCd last version loaded default)

**Ubuntu**:
 - I can ping sites by IP or Name in terminal. 
 - I can input IP in brovser - but see only site name on browser`s top bar.
 - I can`t open any site - only my router setup WEB page!

What the :evil:?

---

### Post by FuriousLettuce on 2006-08-31
Disable IPv6 in Firefox. In Firefox, type in 'about:config' (without the quotes). Search for an entry 'network.dns.ipv6disable' and double click it to set it to true. This will disable IPv6 and your lookups should now work properly.

If you find you are having trouble in other programs, do the following:

```
sudo nano -w /etc/modprobe.d/blacklist-ipv6
```

and in the file insert the following code:

```
blacklist ipv6
```

Reboot, then check it hasn't been loaded by doing

```
lsmod | grep ipv6
```

That should sort out your issues :-)

---

