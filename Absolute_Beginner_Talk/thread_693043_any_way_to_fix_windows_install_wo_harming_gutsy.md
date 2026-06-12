---
title: "any way to fix windows install w/o harming gutsy ?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Adahn on 2008-02-10
course of events:
dual boot xp/gutsy machine...
replaced mobo/xpu/ram and gutsy transitioned beautifully like nothing happened.

The windows install is borked of course....can't even get safe mode.
Will 'repair' from the xp boot disc ruin the gutsy install?

---

### Post by gate on 2008-02-10
As far as I know, windows will repair its install and might **overwrite the boot sector** which will break GRUB. You can then use the Ubuntu disk to fix GRUB, but it shouldn't touch the Gutsy partition itself unless you tell it to.

---

### Post by oldb0y on 2008-02-10
I'm not 100% sure, but I think it only does changes to your XP partition.

---

### Post by benfindlay on 2008-02-10
That depends upon what has gone wrong with your install. If the Master Boot Record for windows has been shot, the only way to repair it (that I know of) requires you to boot your XP cd, go into recovery console and type "fixmbr", however doing so will prevent you from accessing the ubuntu install until you then boot the ubuntu cd and reset-up grub again.

The reason this happens is that most people usually already have winblows installed and they make the transition to ubuntu with a dual boot onto another partition/separate drive. When grub installs, it installs into the boot sector of the primary (master) hard drive, which windows is on, In essence, it replaces the normal windows MBR.

Hope this helps!

---

