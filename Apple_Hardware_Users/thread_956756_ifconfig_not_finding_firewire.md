---
title: "ifconfig not finding firewire"
date: 2008-10-23
forum: Apple Hardware Users
---

### Post by Lars Noodén on 2008-10-23
The kernel finds firewire storage devices and mounts them just fine.  What needs to be done to get ifconfig to allow networking over firewire?

---

### Post by cyberdork33 on 2008-10-23
> **Lars Noodén said:**
> The kernel finds firewire storage devices and mounts them just fine.  What needs to be done to get ifconfig to allow networking over firewire?

The module that allows networking over ieee1394 is blacklisted by default because it causes much confusion.

See /etc/modprobe.d/blacklist

---

### Post by stream303 on 2008-10-27
That can trip one up on PPC as well during first install - take it slowly so you don't end up designating your firewire as the ethernet port - make sure it is pointing to the real ethernet hardware.  Been there. :)

---

