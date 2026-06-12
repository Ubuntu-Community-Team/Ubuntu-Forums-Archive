---
title: "Unable to change resolution in preferences"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by Mike S. on 2006-02-26
In the "Screen Resolution Preferences" the resolution seems to be locked on to "640 x 480"  no other resolutions are selectable.

I've performed the following without any success:

Mike

"How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:

Code:
sudo /etc/init.d/gdm stop (or kdm for KDE)
You can do the whole X configuration process by entering:

Code:
  sudo dpkg-reconfigure xserver-xorg
To start Gnome/KDE again:

Code:
sudo /etc/init.d/gdm start (or kdm for KDE)"

---

### Post by o_fortuna on 2006-02-26
[QUOTE=Mike S.]In the "Screen Resolution Preferences" the resolution seems to be locked on to "640 x 480"  no other resolutions are selectable.

I've performed the following without any success:

Mike

"How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:

Code:
sudo /etc/init.d/gdm stop (or kdm for KDE)
You can do the whole X configuration process by entering:

Code:
  sudo dpkg-reconfigure xserver-xorg
To start Gnome/KDE again:

Code:
sudo /etc/init.d/gdm start (or kdm for KDE)"[/QUOTE]
When you did the sudo dpkg-reconfigure xserver-xorg, what did you do when the screen came up asking you about your monitor? Did it give you options for selecting the available resolutions? You should be able to select different items by highlighting them (scrolling over them with the arrows) and pressing the space bar. I seem to remember having several options when I did a reconfiguration of xorg.

---

### Post by Sandlst on 2006-02-27
I noticed when I did the same thing to fix my resolution, the program auto selected some low resolutions-but they were off the screen! As in I had to scroll down in the list of possible resolutions to expand it: they are below your viewing level.  Even though it is suppossed to use the highest setting, this did not work for me when reconfiguring xorg until those three modes were de-selected, then selecting the ones I wanted. So you might want to try that...afterward I was able to select the correct resolution in the menu (although it still started in the default too low res-even though I never selected it, go figure) Hope this fixes it for you!

---

### Post by Mike S. on 2006-02-27
Ah-with a sigh.

Thanks, I didn't hit the space bar to select the resolution.

Mike

---

