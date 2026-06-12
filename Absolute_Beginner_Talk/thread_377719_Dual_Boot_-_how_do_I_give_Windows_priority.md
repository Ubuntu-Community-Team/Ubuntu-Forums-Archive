---
title: "Dual Boot - how do I give Windows priority?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by amosharper on 2007-03-06
Hi,

At the moment, dualbooting, I am prompted to select Operating System on startup. Default is Linux, and I have six seconds to choose WinXP Home.

How do I make Windows my primary booting OS?

Thanks,

- Amos

---

### Post by taurus on 2007-03-06
You change the **default** from 0 to whatever the entry for your XP is in /boot/grub/menu.lst.  Remember, the first entry is count 0 and the second entry is count 1 and so on.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mikewhatever on 2007-03-06
Hi Amos, you'll need to edit you GRUB menu.
> cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo /boot/grub/menu.lst

and change the number indicated by default to that of your Windows entry. [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by amosharper on 2007-03-07
This worked fine. Thanks.

---

