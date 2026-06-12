---
title: "[SOLVED] rEFIt doesn't see linux"
date: 2007-08-04
forum: Apple Intel Users
---

### Post by xIke on 2007-08-04
I'm trying to triple-boot os x, xp, and feisty fawn.  I installed Ubuntu using the alternate cd (the standard CD couldn't start the xserver).  At the end of the install, I skipped GRUB- figured that rEFIt would take care of boot drive selecting and thus GRUB was unnecessary.

rEFIt doesn't see my ubuntu install.  It only shows my mac and xp partitions as boot choices.  What do I need to do to get ubuntu to show up on that menu?  I'm fine with reinstalling/whatever...I'm just not finding any answers in the numerous threads about this.

Thanks,
-xike

---

### Post by Elv13 on 2007-08-04
How can rEFI see your linux if it dont know where is kernel and root device? Just install grub and it will work.

---

### Post by cyberdork33 on 2007-08-05
> **xIke said:**
> I'm trying to triple-boot os x, xp, and feisty fawn.  I installed Ubuntu using the alternate cd (the standard CD couldn't start the xserver).  At the end of the install, I skipped GRUB- figured that rEFIt would take care of boot drive selecting and thus GRUB was unnecessary.

You assume incorrectly.

---

### Post by xIke on 2007-08-05
Yeah, reinstalled with GRUB and it works great now.  Thanks all.

---

