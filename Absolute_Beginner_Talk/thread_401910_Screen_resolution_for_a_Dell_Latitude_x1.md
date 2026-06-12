---
title: "Screen resolution for a Dell Latitude x1"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by intera on 2007-04-05
Hi,

I've just installed Ubuntu 6.06 in my notebook Dell Latitude X1. It usually uses a 1280 x 1024 screen resolution. The problem is that I go to System -> Preferences -> Screen Resolution and I just can choice 1024 x 768 resolution. There are no other resolutions.

I tried to find a Linux graphic driver in the Dell site but there isn't any for this computer. What can i do?

Thanks!

---

### Post by Kobalt on 2007-04-05
Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

---

### Post by heimo on 2007-04-05
If that doesn't help, see this HOWTO for more information: (if it's frightening, don't hesitate to ask):
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by intera on 2007-04-05
Thanks kobalt.

I've done what you told me exactly. I open the terminal, type "sudo dpkg-reconfigure -phigh xserver-xorg", press enter and the screen gets black and some symbols appear. This happens for a couple of seconds and then everything is like before.

best

---

