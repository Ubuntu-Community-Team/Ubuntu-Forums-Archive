---
title: "640x480 after installing Envy"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ajgoyt on 2008-04-15
Geez this is kind of irritating - I just moved my computer from a 19" monitor to a 37" westy and my drivers got tweaked somehow - after multiple reboots etc - i installed the envyscript and the only rez i see is 640x480, The nvidia settings see my Westy and the Geforce 8400gs, do i need to edit the xorg.conf or what?  also i noticed that it says your hardware does not need and resticted drivers if i try and click into them!

---

### Post by jasonlfunk on 2008-04-15
Try running
```

sudo dpkg-reconfigure xserver-xorg

```

It will walk you through configuring your xorg settings, including resolution.

---

