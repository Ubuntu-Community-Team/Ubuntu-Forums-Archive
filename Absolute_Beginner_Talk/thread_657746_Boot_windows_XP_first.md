---
title: "Boot windows XP first?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Roy :-) on 2008-01-03
can I get grub to boot windows XP by default insteed of linux?
This is until I can sort out Ubuntu to work correctly with my system.

---

### Post by overdrank on 2008-01-03
> **Roy :-) said:**
> can I get grub to boot windows XP by default insteed of linux?
This is until I can sort out Ubuntu to work correctly with my system.

HI and this link is a good source
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)
Good luck!

---

### Post by iansane on 2008-01-03
startup manager in ubuntu, find it in add/remove or synaptic I can't remember but it's in one of them. Some of it is a little complex but easier than manually editing. You can set the default os to boot and customize the look of the menu too.

---

### Post by p_quarles on 2008-01-03
Manually editing the GRUB menu is actually pretty easy if you get good directions. If you want to post your menu configuration file, I can tell you exactly what to change. 

Easiest way to get it is to open a terminal and run this:
```
sudo cat /boot/grub/menu.lst
```
Then, cut-and-paste the output here. (note: that's lower-case LST at the end -- not 1st)

---

