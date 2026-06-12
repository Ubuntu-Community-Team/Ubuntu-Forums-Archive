---
title: "Samba with two NICs?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by bazsl on 2007-01-03
I have 6.10 server on a machine with two network cards. Am I correct that I need the following entries in smb.conf for Samba to work with both NICs?

interfaces = eth0
interfaces = eth1

or should it be 

interfaces = eth0, eth1

The docs are not clear on this (at least what I could find).

Thanks.

---

### Post by bazsl on 2007-01-03
FWIW using a separate entry for each NIC seems to work.

---

