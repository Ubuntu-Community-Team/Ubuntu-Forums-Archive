---
title: "Curious Monitor Issue"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by jeffk14 on 2008-01-31
I installed Xubuntu 7.10 on an old Gateway computer hooked to an old emachines 17" crt monitor. All went well, but then I changed out monitors to an older "Hansol" 15" crt monitor & the monitor would crash when trying to load the gui. I ran "lshw" from the terminal & found that the system still "thought" that the emachines monitor was still hooked up. **Being the newbie that I am**, I just reinstalled Xubuntu with the 15" monitor hooked up and now everything works. Is there a better (quicker) fix for this in the future? The comp is an old gateway 333mhz processor, 256mb ram, with an old pci video card that I grabbed out of a box full of junk parts. Thanks.

---

### Post by benfindlay on 2008-01-31
Yes, type ```
sudo dpkg-reconfigure xserver-xorg
``` into a terminal window and just follow the prompts on screen!

Hope this helps!

---

