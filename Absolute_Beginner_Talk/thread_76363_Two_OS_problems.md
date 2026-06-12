---
title: "Two OS problems"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by bayou64 on 2005-10-15
I installed Ubuntu 5.04 without any problems on 15GB of my 40GB HD. GRUB loaded on every boot. Then I decided to install Windows 98 on 20GB of partition. Windows start fine, but GRUB no longer comes up. How do I get GRUB to come up again? I have tried (sort of) to reinstall GRUB, but the UBUNTU setup wants me to totally clear the HD to do that. Is there any other way?

---

### Post by marsian on 2005-10-15
The reason is that Windows considers itself as the only OS on earth , thus it overrides the MBR of the disk.
Follow the following "tutorial" and your GRUB menu will be set back (allowing to choose Ubuntu or Windows)
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)
Manu.

---

