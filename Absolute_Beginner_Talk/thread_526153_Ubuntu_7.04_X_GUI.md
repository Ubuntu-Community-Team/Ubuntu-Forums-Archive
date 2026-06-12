---
title: "Ubuntu 7.04 X GUI?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-08-15
Last time I tried Ubuntu 7.04, I had the problem of having a bug within Ubuntu that meant my ATI Radeon Xpress 200M Graphics Card wasn't working with the X GUI thing and so I had to remove linux.
But I was reading this site about the way I'm meant to install it, using the alternate install disc but coulnd't I just do this?:
[http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

Because I got to that last time but didn't know what to do, or do I have to use the alternate disc?

---

### Post by renzokuken on 2007-08-15
you could install it anyway, if X crashes, switch to a TTY terminal (Ctrl+Alt+F1) and the run

```
sudo dpkg-reconfigure xserver-xorg
```

selecting the "vesa", "ati" or "radeon" driver (all should work with your card)

then restart X

---

### Post by SamTyson92 on 2007-08-15
> **renzokuken said:**
> you could install it anyway, if X crashes, switch to a TTY terminal (Ctrl+Alt+F1) and the run

```
sudo dpkg-reconfigure xserver-xorg
```

selecting the "vesa", "ati" or "radeon" driver (all should work with your card)

then restart X

Thanks I might give it a shot soon then!

---

### Post by rocknrolf77 on 2007-08-15
If you try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
You don't have to go thru so many steps to pick the vesa driver.

---

