---
title: "Grub Error 17"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-07-31
I've had a machine running Fedora 6.  I decided to install Ubuntu Dapper Drake as a backup OS for a Dual Boot.  FC6 uses a logical volume management.  I installed Ubuntu onto hdd2 partition. Now I get Grub 17.  Where do I go from here?

---

### Post by pollywog on 2007-07-31
I recently had a similar problem. Are you saying that you have 2 hard drives, and installed ubuntu on the 2nd (slave)? If so ubuntu probably wrote grub to the MBR of the wrong hard drive. I went into BIOS at boot up, and changed the boot order of the hard drives, and that fixed the problem in my case- Good Luck

---

