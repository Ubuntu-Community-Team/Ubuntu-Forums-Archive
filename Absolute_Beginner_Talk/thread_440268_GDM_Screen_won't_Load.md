---
title: "GDM Screen won't Load"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by DRoll221 on 2007-05-11
Hello all...I tried to install Compiz yesterday on Edgy, and after a reboot the GDM screen won't load.  I get a black and white screen (almost like really small chain link pattern) and the timer cursor just sits there spinning forever.  Is this due to a compiz error or is it something else?

---

### Post by finer recliner on 2007-05-11
if compiz was the LAST thing you changed before rebooting. than yeah, definitely its fault. 

boot into recovery mode and undo any changes you made to your system before the screen error.

---

### Post by DRoll221 on 2007-05-11
could you explain how to do this further? thank you

---

### Post by finer recliner on 2007-05-11
when you turn on the computer and GRUB loads, it will ask you what you want to boot. there should be an option for your kernal with recovery mode. by choosing this, you will log in as root at a terminal immediatly even before X loads. this will give you chance to make any changes to the system before normal boot. uninstall compiz and whatever else you changed before the problems started

---

