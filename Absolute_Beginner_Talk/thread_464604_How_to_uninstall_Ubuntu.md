---
title: "How to uninstall Ubuntu"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-04
No I realy don't want to uninstall Ubuntu.This just hit me today some guy wanted to uninstall Ubuntu and somebody posted how Ubuntu will destroy your mastor boot record and then I realized a while back when I crippled Ubuntu once so I poped in th G partitoner and deleted my Ubuntu partion to reinstalit well I forgot to hit F12 to boot of the Linux live cd and it went rite into windows with know problems.So if Ubuntu does this deletes your Mastor Boot Record how come it did'nt do it to mine.

---

### Post by nofrak on 2007-06-04
If you still have windows installed, boot into it from GRUB, then open up a command prompt and type FIXMBR.  If not, windows will overwrite the mbr when you install it.

---

### Post by starcraft.man on 2007-06-04
> **jonward0690 said:**
> No I realy don't want to uninstall Ubuntu.This just hit me today some guy wanted to uninstall Ubuntu and somebody posted how Ubuntu will destroy your mastor boot record and then I realized a while back when I crippled Ubuntu once so I poped in th G partitoner and deleted my Ubuntu partion to reinstalit well I forgot to hit F12 to boot of the Linux live cd and it went rite into windows with know problems.So if Ubuntu does this deletes your Mastor Boot Record how come it did'nt do it to mine.

Ummm, I dunno. Depends how you had Ubuntu installed... if you had installed GRUB to the Ubuntu partition then it didn't overwrite your MBR and you could have just booted up properly. 

The person your referring to was likely trying to get at the fact that installing Ubuntu in the default manner will overwrite the MBR of the main drive usually, unless otherwise specified.

---

### Post by jonward0690 on 2007-06-04
No my computer is working just fine.What I am saying is people say if you delete Ubuntu you won't be able to boot into windows because it has destroyed your MBR well they must be wrong because when I broke Ubuntu I deleted it and I could still go into windows just fine.

---

### Post by jonward0690 on 2007-06-04
> **starcraft.man said:**
> Ummm, I dunno. Depends how you had Ubuntu installed... if you had installed GRUB to the Ubuntu partition then it didn't overwrite your MBR and you could have just booted up properly. 

The person your referring to was likely trying to get at the fact that installing Ubuntu in the default manner will overwrite the MBR of the main drive usually, unless otherwise specified.

Well the way I had Ubuntu installed was using the live cd using the first option.

---

