---
title: "Dual-booting Feisty with XP, cant get to grub"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by meisbored on 2007-08-09
Since I needed SATA drivers which I was unable to get until the next day in order to install WinXP after wiping my hard drive, I went ahead and installed Feisty first, and left a big partition for Windows. Now that I have installed Windows, it automatically boots XP instead of going through the GRUB loader. Is there any way I can edit something in XP to make it boot to the GRUB loader first so that I can access Ubuntu?

---

### Post by splintercellguy on 2007-08-09
Burn the Super GRUB CD from here and use it to restore GRUB: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) Windows has a habit of overwriting foreign boot loaders.

---

### Post by phr0ze on 2007-08-09
Grub was wiped out by XP, You need to set it up again. Someone else may know the steps. Sometimes its just easier to install ubuntu again.

---

### Post by skymera on 2007-08-09
or simply reinstall grub using LiveCD :)
ave times and fuss!

---

