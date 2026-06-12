---
title: "nvidia GeForce MX4000"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by drako1011 on 2007-04-19
I'm kinda new to linux, and i just installed feisty. I have a nvidia GeForce MX4000 and I can't get the resolution to go past 800x600. How do I fix this? Do I need to install certain drivers?

Thanks

---

### Post by tbg58 on 2007-04-19
On Edgy or Feisty, you should be able to choose Applications, Add/Remove, then type in nvidia and you should be able to select nvidia legacy drivers.  This should get you up to full screen resolution.
Hope this helps!

---

### Post by PurplePenguin on 2007-04-19
As far as I know, getting 3D acceleration working doesn't necessarily mean that the resolution will be upped.  I've got an MX4000 on Edgy and had to run:
```
sudo dpkg-reconfigure xserver-xorg
```
in order to select a higher resolution.  Edgy wouldn't let me pick anything higher than 1024x768 unless I go through this.

---

