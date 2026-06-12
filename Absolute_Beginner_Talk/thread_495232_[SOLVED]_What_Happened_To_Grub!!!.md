---
title: "[SOLVED] What Happened To Grub!?!??!?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by -=Viper=- on 2007-07-07
Ok i reloaded windows XP and after i reloaded it i rebooted and waited for grub but it never came :S  the partision is still there but grub did not load!!  What can i do to fix it other then a fresh install (it would be a pain for a fresh install)

---

### Post by taurus on 2007-07-07
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by atria on 2007-07-07
You can repair grub by following the linkposted by taurus.

On a sidenote, grub is not loaded because Windows had overwritten the MBR (Master boot record) that grub was installed in.

All you need to do is to reinstall grub using a livecd.

Hope that helps

---

### Post by splintercellguy on 2007-07-07
Super GRUB CD too.

---

### Post by -=Viper=- on 2007-07-07
> **splintercellguy said:**
> Super GRUB CD too.
THAT WORKED!!! thanks man!  now i just have to fix windows -_- (stupied million updates :P)  thanks everyone :D

---

