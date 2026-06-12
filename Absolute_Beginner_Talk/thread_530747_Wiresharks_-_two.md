---
title: "Wiresharks - two?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-20
I installed Wireshark network tool from the add/remove programs. It installed two versions displayed in the menu as:

Wireshark
Wireshark (as root)

I can get the "Wireshark (as root)" to work fine, it detects my eth0 port, but the other one won't detect a port. Why does it install the "Wireshark" version and the "Wireshark (as root )" version, if the only one that works is the "Wireshark (as root) version?

---

### Post by splintercellguy on 2007-08-20
The normal Wireshark will not allow packet capture, since that is something only root can do. It is simply there to let you view previously captured data.

---

### Post by mikex on 2007-08-20
> **splintercellguy said:**
> The normal Wireshark will not allow packet capture, since that is something only root can do. It is simply there to let you view previously captured data.

Oh I understand, thanks!

---

