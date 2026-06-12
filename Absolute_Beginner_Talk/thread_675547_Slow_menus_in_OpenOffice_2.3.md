---
title: "Slow menus in OpenOffice 2.3"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-01-22
I don't know if this is the right forum for this problem.

OOO menus are very slow to unfold in Metacity and normal when I launch OOO in Compiz (Nvidia/Xgl). Other applications run normally with both window managers.

Any suggestions?

Thanks

Laurent

---

### Post by ajmorris on 2008-01-22
hi there, could you try loading the OOo component in question via the CLI, and posting any output from the CLI here?
Also, is it with all OOo components, or just a particular one?

---

### Post by lduplantie on 2008-01-22
Started Writer and Calc from the terminal. No messages in the terminal. Same sluggish performance. It seems its with all components.

---

### Post by lduplantie on 2008-01-23
t looks like I may have found the problem. I uninstalled xserver-xgl with Synaptic.

The menus are now back to normal. Incidentally, I now notice that the cursor blinking speed in this Message window is also back normal speed and the font back to normal size (used to be smaller).

However, the cube rotation did not work anymore. I enabled the hardware acceleration (Nvidia Quadro2 32-MB). Compiz would not run before with this configuration. Surprisingly, now it does.

I looking for a solution I uninstalled the Ubuntu-OpenOffice to install the "official" version. With xserver-xgl, even the official version had slow menus.

Since I am in "learning mode" might as well try re-installing the Ubuntu version of OOo to see if there is any interaction there.

Your comments would be appreciated.

---

### Post by lduplantie on 2008-01-23
Re-installed the Ubuntu version. Works normally. Compiz is also working.

---

