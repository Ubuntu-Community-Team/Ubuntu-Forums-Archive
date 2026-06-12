---
title: "ubuntu screen problem"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by cvance383 on 2008-03-31
Hey my name is Collin Vance. I have been using ubuntu since about november. The other day I attempted to watch one of my movie's on my home LCD screen, my LG TV. I went to screens and graphics menu. And diddled with it, well some how I really messed things up. Now if I turn on my laptop it takes me to basically a terminal screen. But if i plug in the TV, monitor cable, it will go crazy, then a popup will say something about screen resolution, asking if i want to continue, configure, or shutdown. well I tried searching here and google, but i couldnt get this problem to go away. How can I fix this whole screen problem, I dont even mind reinstalling ubuntu, but I don't have the cd to do it, nor any blank cd's sitting around. Can anyone help with the problem, and yes I have searched and tried some answers. I just want my screen resolution to be back to it old resolution, and to be able to boot without having a monitor cable plugged into my laptop.

---

### Post by cvance383 on 2008-03-31
ttt

---

### Post by Patness on 2008-04-01
My personal experience suggests that Screens and Graphics is an especially unreliable program. I can make all the changes I want and I just get stranger and stranger results. It can't even detect my monitor, and when I try to change the settings with any authority it reverts back to some other setting.

Post your /etc/X11/xorg.conf file here, and I'll see what I can do.

---

### Post by xeth_delta on 2008-04-01
Hi Collin, welcome to the forums. I agree with Patness, womething is wrong with the xorg,conf file.
I guess that you could start by reconfiguring the X server. To do so, start by making a backup of the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
Then
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the on-screen instructions.
Good luck and let us know if you need further help.

---

