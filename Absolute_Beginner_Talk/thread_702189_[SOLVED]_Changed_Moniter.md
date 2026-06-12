---
title: "[SOLVED] Changed Moniter"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-02-20
Hi to all.
I bring my hard disk from home to office to update some ubuntu softwares from internet.
So the profil is changed for ubuntu.
Now it picks up the moniter but the display is too much small.That i cant see any thing.
How could i change the resolution without going to ubuntu.
PLease urgent help.

Thanks in advacne.

---

### Post by Kilz on 2008-02-20
> **mmarif4u said:**
> Hi to all.
I bring my hard disk from home to office to update some ubuntu softwares from internet.
So the profil is changed for ubuntu.
Now it picks up the moniter but the display is too much small.That i cant see any thing.
How could i change the resolution without going to ubuntu.
PLease urgent help.

Thanks in advacne.

boot into safe mode, it should come to a command prompt. Type ```
sudo dpkg-reconfigure xserver-xorg
``` This will configure your display, for the most part keep hitting ok . You will finally get to a list of resolutions. Deselect the high ones by moving up and down the list with the arrow keys and deselecting with the space bar. Finish the rest by clicking ok, then restart your system.

---

