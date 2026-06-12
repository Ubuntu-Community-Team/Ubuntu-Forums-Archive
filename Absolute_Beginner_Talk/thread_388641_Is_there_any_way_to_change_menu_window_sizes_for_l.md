---
title: "Is there any way to change menu window sizes for low-resolution PCs?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by jerseyboy91 on 2007-03-19
I have a laptop running Xubuntu 6.10, but the old computer limits the computer resolution to 800x600. A lot of the Xubuntu settings and application menus are cut off because of the low resolution, and there's no way for me to see what in the menu was cut off from the screen. Is there any solution for making menu windows smaller for computers with low resolution screens?

---

### Post by benfindlay on 2007-03-20
Is your laptop's actual maximum resolution only 800x600 (i.e. will it run higher in windows?)

If so it would be worth you reconfiguring your X to run higher resoltuions. To do this type ```
sudo dpkg-reconfigure xserver-xorg
``` in terminal and follow the on-screen guidelines. When you get the part where you can add extra supported resolutions, you use arrow keys to navigate the list, space bar to add the extra ones in and enter when you have finished!

Hope this helps!

---

