---
title: "grub"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by fusuke on 2006-07-25
hi guys.. 

i just want to ask something related with grub. 
i m new with ubuntu and running dapper drake. 
i have winxp pro on my hd but the installation is corrupted. 
what will happen if i reinstall winxp? 
will the installation wipe out grub in the mbr?

any solution guys?

thanks

---

### Post by sgbeamer on 2006-07-25
It will but it's not much of a problem. All you have to do to get grub back is boot off the cd in "rescue mode", mount your Ubuntu partition, chroot to that partition and run grub-install /dev/sda (/dev/hda) and it will put it back.

Before you do that try to boot up Windows in Safe mode and restart it after it has come up in safe mode (if it will).  This often fixes a corruption problem on my wife's XP machine.

---

