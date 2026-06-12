---
title: "Dual Boot Downgrade Question"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2008-03-23
I have Vista and Ubuntu installed with the grub loader.

I want to reformat the vista partition and install XP instead.

How do I go about doing this without loosing the grub loader?

Thanks

Seek

---

### Post by Regel on 2008-03-23
Not possible, XP will overwrite MBR. You have to reinstal/reconfigure GRUB (not whole Ubuntu, luckily).

Here are working instructions. Remember to backup all valuable data before installing a new os - just in case.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

