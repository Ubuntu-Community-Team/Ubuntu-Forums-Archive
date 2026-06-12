---
title: "Backtrack 5 R3"
date: 2013-10-12
forum: Any Other OS
---

### Post by Ft3Brpm on 2013-10-12
Hi.
I had a computer running dualboot Ubuntu 12.04 and Windows 8. I then tried to install Backtrack 5 R3 (not through virtualbox). It seems to have used up the partition of my hard drive I installed it to (50gb partition), but there is no option to boot to it from GRUB. Is there perhaps a command in the GRUB command line I can use to access it? It says it's on sda10.

---

### Post by oldos2er on 2013-10-12
Moved to Other OS/Distro Support.

Have you tried ```
sudo update-grub
```?

---

