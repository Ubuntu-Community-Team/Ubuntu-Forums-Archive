---
title: "Installed, rebooted, then 'shimmerring yellowish screen'?"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by ntu on 2005-10-05
Hi All,
I have installed Ubuntu 5.04 and after reboot get to a 'shimmerring yellowish screen'? It has a vaguely discernable shimmering "Ubuntu" on it.
I have a Dell GX110 with 96mb of ram.

---

### Post by Ampersand on 2005-10-05
Try pressing ctrl, alt and + to cycle through the resolutions.

---

### Post by ntu on 2005-10-05
Thanks for the great advice Ampersand, a lovely login screen now. 

However, when I reboot I get back to the shimmering screen and need to cntl alt + again?

And after I login I get to a screen with no icons, taskbar, etc? It looks lovely though.

---

### Post by Ampersand on 2005-10-05
Try right clicking on a desktop, then select 'open terminal' from the menu that appears. Run 'gnome-panel' from the terminal, and you should get a couple of bars at the top and bottom of the screen.

If this works, you can correct the resolution problem. In the System menu that hopefully appeared, go to Preferences, and then Screen Resolution. Set the highest resolution that works as the default. 

It's possible that you might not have enough memory for Gnome to be useable. Try following through the howto here: [https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport) to install XFCE.

---

### Post by ntu on 2005-10-06
Thanks Ampersand.
I put in 128mb of ram and rebooted.
I right clicked on the desktop and selected 'open terminal'. There was no menu and no gnome panel?

---

### Post by matthewv on 2005-10-06
once in the terminal type
```

gnome-panel

```
and press enter

---

### Post by ntu on 2005-10-06
Thanks for the great help guys. Have now got a suitable resolution saved in the system menu under preferences/screen resolution, and the machine automatically reboots into that resolution after logging in. 
However on rebooting I still have to do a few ctrl alt + 's to get to the login prompt?

---

