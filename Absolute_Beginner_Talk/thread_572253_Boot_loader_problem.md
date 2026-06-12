---
title: "Boot loader problem"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-10-10
Hi there, Ive been doing a dualboot of XP/ubuntu for a while but i needed to remove ubuntu which i did from within windows using the drive manager or whatever.

Anyway, now when my computer boots up it has a grub loader error because ubuntu is no longer there. I put in the xp disc and went to recovery console but settings do i need to change in order to make it boot to windows xp and not boot to the grub loader?

---

### Post by phr0ze on 2007-10-10
I'm not sure, I'd try to just get grub to not look for ubuntu and make windows the default choice. Probably safer and no problem for windows to leave grub there.

---

### Post by ukulele_ninja on 2007-10-10
how do i do that?

---

### Post by ukulele_ninja on 2007-10-10
nevermind just got it! had to do fixmbr. Thanks!

---

