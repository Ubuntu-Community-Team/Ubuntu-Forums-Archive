---
title: "[SOLVED] How to resolve an IP address from name, works in SMB but not ping?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Contrarian on 2007-12-01
SMB is able to connect to a machine on my network by name.  But when I ping, the name will not resolve to an IP address.  How can I determine the IP address from within samba?

---

### Post by dgray_from_dc on 2007-12-02
You probably have a WINS server somewhere in your network.  WINS provides name resolution in SMB.  I have no idea how to get the IP address from SMB.  You could always check your DHCP server e.g. your router.

---

