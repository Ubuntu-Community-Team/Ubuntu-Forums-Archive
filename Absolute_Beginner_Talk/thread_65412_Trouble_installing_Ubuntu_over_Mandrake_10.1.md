---
title: "Trouble installing Ubuntu over Mandrake 10.1"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by jacatone on 2005-09-13
I already have a dual boot setup with WinXP and Mandrake 10.1 using Lilo. I'd like to just write over Mandrake with Ubuntu. I've got this small ext. 3 partition where Mandrake currently lives. How do I configure the installer to do this change over? Thanks.

---

### Post by ispmarin on 2005-09-13
You can just install ubuntu on the mandrake partition and let grub control the boot procedure. Grub will find your WinXP partition on the installation process and let the dual boot.

Ivan

---

### Post by jacatone on 2005-09-13
Apparently not. When I select the Mandrake partition nothing happens. I read something in the setup that said Ubuntu will not install over an existing Linux partition.  Am I supposed to delete the Linux partition first then start over?

---

### Post by aysiu on 2005-09-13
During the installation process, just select "manually edit partition table" and select the Mandrake partition to be overwritten.

---

