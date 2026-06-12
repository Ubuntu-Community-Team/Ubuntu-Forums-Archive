---
title: "Any other way to run WindowsXP"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-04-27
Any other way to run WindowsXP on Feisty other than VMplayer or VMserver?

---

### Post by lamalex on 2007-04-27
VMworkstation, virtualbox, qemu. TONS of virtualized environments.

---

### Post by Repent on 2007-04-27
Feisty not letting run any VM software so I need something else.

---

### Post by psionyk on 2007-04-27
If you're referring to other virtualization software, you can use VirtualBox or qemu.  If you're only looking to run a few specific programs from Windows then the obvious choice would be WINE/Cedega, depending on whether the software is compatible.  I'm not aware of a different way to run Windows XP in its entireity or individual programs than these from within Feisty.

Let us know what you're looking to use Windows for, and perhaps we can suggest some alternative progs...

Hope this helps!

---

### Post by lamalex on 2007-04-27
for feisty, vmware server doesn't work. you need to use vmware workstation 6 beta. It's free on their site.

---

### Post by starcraft.man on 2007-04-27
> **Repent said:**
> Feisty not letting run any VM software so I need something else.

You can always make a dual boot... they aren't very hard.

However, I think XP needs to be on the C, so if you already put ubuntu on the first slot you might have to reformat.

I prefer a dual boot, no virtualizing overhead then. Also, nother tid bit... if your doing that partition a seperate /home partition so if you upgrade or reinstall anything you got all your files tucked away seperate Ubuntu. And Grub should automatically detect your install of XP if its on C, another cool ubuntu feature.

---

