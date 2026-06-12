---
title: "Is it too late to Dual Boot?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-05-27
I installed Ubuntu 7.04 and simply love it so far.  It saw my hardware without any difficulties.

When I did the install, I selected my entire hard drive, wiping out my Windows XP.  NOW I realize I may have been too hasty.... because there are some Windows programs that I need that WINE can't handle.  So if I need to start over and install WindowsXP first, then Ubuntu, so be it. :)

BUT.... is there a way to re-partition my Ubuntu installation and THEN reinstall WindowsXP?

Thanks! :)

---

### Post by yabbadabbadont on 2007-05-27
As long as you don't need to run 3d games, you might consider running windows inside of a virtual machine using either vmware or virtualbox.  If you do resize your partition and reinstall windows, you will need to reasearch how to restore the grub boot sector afterwords as windows will probably overwrite it during the installation.

---

### Post by bone43 on 2007-05-27
> **ElEdwards said:**
> I installed Ubuntu 7.04 and simply love it so far.  It saw my hardware without any difficulties.

When I did the install, I selected my entire hard drive, wiping out my Windows XP.  NOW I realize I may have been too hasty.... because there are some Windows programs that I need that WINE can't handle.  So if I need to start over and install WindowsXP first, then Ubuntu, so be it. :)

BUT.... is there a way to re-partition my Ubuntu installation and THEN reinstall WindowsXP?

Thanks! :)

 I would wipe the drive repartion give your self enough room for windows and leave the rest free space.
Install XP then install Ubuntu using the free space.

---

### Post by yabbadabbadont on 2007-05-27
> **bone43 said:**
> I would wipe the drive repartion give your self enough room for windows and leave the rest free space.
Install XP then install Ubuntu using the free space.

That would be the easiest route to take.

---

### Post by Drakkor on 2007-05-28
yeah,windows doesn't play well with other os's, it needs to be the only one on the drive, but you can just use something like the GParted Live CD , to make a partition for C:\ windows os, and install windows first,then leave the rest unallocated,
and reinstall Ubuntu !  ;)

---

### Post by alienexplorers on 2007-05-28
You can make some free space on your drive and load windows.  You just need to reinstall grub to make the system dual boot.  There are plenty of threads showing how this is done.  Just do some searching.

---

