---
title: "network printer setup"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-07-08
Is Samba or some other networking facility required in order to setup a network printer in Ubuntu or is this capability built into the O/S ?

If I want to setup my HP2100 Laserjet so that I can print from any of my 4 computers (all of which will be Ubuntu running thru a hard wired Netgear hub), do I use IPP, SMB, or LPD ?

Thanks.

---

### Post by Apple 101 on 2006-07-08
You would use the option for a Networked printer (tick the box on one of the other computers to search for it) or use the Linux print option (not sure what the name is).

---

### Post by wpshooter on 2006-07-08
> **Apple 101 said:**
> You would use the option for a Networked printer (tick the box on one of the other computers to search for it) or use the Linux print option (not sure what the name is).

But would I have to have SAMBA setup on each of the computers or is this capability already built into Ubuntu ?

Thanks.

---

### Post by Apple 101 on 2006-07-08
Edit your cupsd.conf file (not sure where it is exactly, so search for it).

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.* (change this one to your IP range)
</Location>

---

