---
title: "triple boot problem"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by shadow sk1ll on 2008-01-03
I installed Vista Ult and it was booting fine. then I installed Windows XP, then I installed ubuntu. When I go to boot up in Grub it shows Ubuntu and Vista. I don't see any XP, but, when I go to load up vista it loads xp. In Linux I can see all of the hdds. These installs are all on the same harddrive (psychically). Any ideas on how to fix this? maybe just edit grub or something idk. Anyone know if the problem is I installed xp 2nd, when it should have been 1st?

---

### Post by wjp.reg on 2008-01-03
May have to do with the order of the installs:[ check this out]("http://ubuntuforums.org/showthread.php?t=220452")

---

### Post by indytim on 2008-01-03
Check your /boot/grub/menu.lst.  It sounds like the entries are mis-identified for your Windows ops.  

Note : backup this file before editing.

IndyTim

---

### Post by Fleece Flamingo on 2008-01-03
Most tutorials on dual booting windows vista and xp suggest you install xp first :?

---

