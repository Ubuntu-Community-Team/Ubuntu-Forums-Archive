---
title: "Nbtscan in ubuntu"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Me-262 on 2007-11-16
Hello all. 

I am trying to use Nbtscan to scan my network and get info on the other comp on my LAN.

However, when I use nbtscan to lookup the other computer (192.168.1.2) it gives me this...

```
$ nbtscan 192.168.1.2
Doing NBT name scan for addresses from 192.168.1.2

IP address       NetBIOS Name     Server    User             MAC address      
------------------------------------------------------------------------------
gms@desktop:~$ 
```

As you can see it basically gives me no information at all.

What arguments etc. do I need to include for it to give me info on this other computer?

Thanks

EDIT- I forgot to mention I am running Gutsy

---

### Post by Me-262 on 2007-11-16
Bump.

Anyone got any ideas? 

I haven't had much luck on google.

---

### Post by robfos7 on 2008-07-22
nbtscan -r 192.168.1.2/32

---

