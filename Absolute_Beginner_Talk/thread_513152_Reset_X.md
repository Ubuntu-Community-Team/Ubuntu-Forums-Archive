---
title: "Reset X"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Sain on 2007-07-30
Hi!

Very often, when i (re)install graphics driver and mess around with desktop effects, i get X Server fail to start. Even disabling/enabling some graphics features can crash X sometimes!
Ussually there is message that graphics driver is version xxxx, and it doesn't match version xxxy in the kernel, or something like that...

Now, is there a way to "reset" Xorg settings to default, from recovery console? I now I can reconfigure it, but it's not very simple, and i can't seem to make settings right. 

Cheers!
Sain

---

### Post by mattmole on 2007-07-30
After you do a base install / reconfigure X so it does what you want copy the xorg config file with the postfix "-backup". That way, if X fails you can just copy back the "*-backup" file to the original and X should fire up OK.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

Would that suffice? Use sudo, as you need root privileges to do anything to the xorg.conf file

mattmole

---

### Post by Sain on 2007-07-30
Yes, that'll do the trick. Thanks!

Never thought about making backup, but  this is so simple solution that it's embarrassing :)

By the way, on Gutsy blueprints page I've found project named *bullet-proof-x* which should give Ubuntu ability to start in "safe" graphics mode, even if x fails, so that could simplify recovery in these cases.

[B]
EDIT:[/B]
However, I can't help but asking: why is it so easy to crash X? I mean, on windows I've installed/reinstalled drivers dozen times, but they never crashed because of it... This is not Ubuntu's fault i think it's the X server; same things were happening while I used SUSE.

---

