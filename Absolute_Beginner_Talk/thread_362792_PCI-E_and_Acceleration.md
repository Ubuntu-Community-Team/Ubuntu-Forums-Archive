---
title: "PCI-E and Acceleration"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-02-16
Hi,

I have just installed a new Nvidea card and updated the drivers with the Envy script.  However, it appears the acceleration is not quite up to speed.  Running the Hufo's Tunnel sreensaver, for example, is just about possibe... with blocky graphics.  How do I make Xorg see that my card is a PCI-E card and how may I tweak Xorg to get the most out of my card (GeForce 7300GT)?

Thank you.

---

### Post by Spr0k3t on 2007-02-16
Check your /etc/X11/xorg.conf to see if the driver is set to use "nv" or "nvidia".  The latest drivers would not install for me using Envy, I had to use the method written by PriceChild.

I just tested Hufo's Tunnel on a laptop with Intel 915 chipset and it runs smooth, nowhere near my desktop PC at home, but still smooth.

---

### Post by Norfolk 'n' Good on 2007-02-16
My Xorg is set to 'nvidea'.  Could you post a link to this PriceChild please.  Thanks for a speedy response.

---

### Post by Spr0k3t on 2007-02-16
Go to Step 2 Option 2 and follow along (stop before step 3)

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

You may want to print the information out completely as I had to finish the process through runmode 2 to get it working.

---

