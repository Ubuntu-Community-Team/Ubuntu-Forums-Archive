---
title: "[SOLVED] DHCP server fail!!!"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by adi82 on 2007-11-19
After shutting down my laptop, i get 
**DHCP server  ([COLOR="Red"]fail[/COLOR]) **
and a lot of things that i cant read because shutting down is completed.

what is DHCP serve and why is not working?

p.s.: i don't have any problem with my internet connection and i am using cable network from direct line.

---

### Post by santiagoward2000 on 2007-11-19
> **adi82 said:**
> After shutting down my laptop, i get 
**DHCP server  ([COLOR="Red"]fail[/COLOR]) **
and a lot of things that i cant read because shutting down is completed.

what is DHCP serve and why is not working?

p.s.: i don't have any problem with my internet connection and i am using cable network from direct line.

You made me realize I get the same messages too. I hadn't noticed before, and everything seems to be working fine here...

---

### Post by adi82 on 2007-11-19
> **santiagoward2000 said:**
> You made me realize I get the same messages too. I hadn't noticed before, and everything seems to be working fine here...

i forgot that sometimes it does not fail.:confused::confused:

---

### Post by mellowd on 2007-11-19
DHCP = Dynamic Host Configuration Protocol.

Essentially a DHCP server leases out IP addresses. A home router is generally acts as a dhcp server because it leases out an ip address to any computer connecting to it. Your linux machine/server can also do the same. If you have your machine connected directly to a router or modem then you don't need the server part, you'll only need to set up your interface to use dhcp to get an ip address, thereby getting the dhcp server in your router to lease out the address

---

