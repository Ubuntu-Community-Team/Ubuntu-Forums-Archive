---
title: "Boot loader question"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-03-22
Hi,

In GRUB I see two Ubuntu Kernels (so 4 ubuntu entries all together)

I didn't install twice, but I did run a live CD before installing.  

Should I delete one of these entries?

---

### Post by darrenrxm on 2006-03-22
No do not touch anything. That is how a normal install grub is supposed to look. Or so I have been told. Just let it boot into the first entry in the grub menu. And you will be set.

---

### Post by mcduck on 2006-03-22
If you have older kernel versions, you can uninstall them with Synaptic after you have confirmed that the new one works fine. Uninstalling old kernels also removes the entry from Grub :)

---

### Post by brandoncolorado on 2006-03-22
Ok cool.

Thanks for the info.

Only one installation here.  First time Linux user :mrgreen:

---

### Post by OffHand on 2006-03-22
[QUOTE=brandoncolorado]Ok cool.

Thanks for the info.

Only one installation here.  First time Linux user :mrgreen:[/QUOTE]
Did you upgrade? After an upgrade it shows 4 entries. It's save to remove the obsolete entries in the grub. Be careful though. Don't screw up  ;)

---

### Post by alamba on 2006-03-22
An upgrade would pull down a new kernel if available. Rather than deleting the older kernel I would suggest that you put a hash (#) in front of the older kernels in menu.lst. This would give you the flexibility of back tracking incase needed later.

A

---

### Post by brandoncolorado on 2006-03-22
Thanks guys,

Nope I never upgraded.  To be quite honest I'm not sure where they extra entries came from.  I will take the safe route here until I get a bit better with this awesome operating system.

---

