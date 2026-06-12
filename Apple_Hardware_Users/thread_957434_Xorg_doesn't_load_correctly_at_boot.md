---
title: "Xorg doesn't load correctly at boot"
date: 2008-10-24
forum: Apple Hardware Users
---

### Post by dustynus on 2008-10-24
After a fresh install and now using lilo instead of grub, it seems once I boot, I just get a screen with the X cursor and it's a black background. I'm using E17, no gdm.
I have to alt-F1 to go to command and do the following to get xorg to load properly:

sudo killall Xorg
sudo rm /tmp/.X0-lock
startx

and It then works fine. Other than doing this, it will just sit at the screen with the mouse cursor and not load anything!

Is there any ideas to fix this ?

Running a Macbook2,1 2G, triple boot

---

