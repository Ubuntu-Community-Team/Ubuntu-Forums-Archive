---
title: "Ubuntu boot up"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by Maggot(8) on 2005-07-14
How do you remove the boot up thing that installs with ubuntu?  I have a drive with WindowsXP and I want the computer to boot straight into windows like it used to before I installed Ubuntu.

---

### Post by codejunkie on 2005-07-14
insert your windows xp cd,*** it cannot be a windows xp recovery cd*** it has to be a regular windows xp cd. boot from it and choose recovery console when you get to the recovery console, which is just a command prompt type ```
fixmbr
``` that should reinstall the default windows xp boot loader. and make sure you backup data before you do this because things can always go wrong when you can't afford them to.

---

### Post by Maggot(8) on 2005-07-14
Nevermind I got it.  I found a topic about grub that solved my problem.  Thanks anyway.

---

