---
title: "Driver Question"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by voiceofxile on 2006-06-05
I used aptitude from the kernal recovery command promt to download and install xserver.org as well as a restricted driver: fglrx .     How do I implement this driver for use, instead of the current driver Linux loads? How can i be sure xserver is installed?

My problem is that after I log in, the system freezes. I believe this is due to my graphics card.

---

### Post by rado_london on 2006-06-05
Check your /etc/X11/xorg.conf file. It has the configuration for the graphics and the whole X server. You can make a search on the forums for changing and editing it. Good luck

---

### Post by Burke on 2006-06-05
First, run this: 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot, and make sure it all works.

Now when you're logged in (normal boot, go into gnome), open up a terminal and type:

```
sudo apt-get install fglrx fglrx-control
```

Then, I think it's a simple matter of typing:

```
sudo aticonfig --initial
```

...and rebooting.  


Before you do any of this, make sure you actually have an ATI card. There are different drivers for the NVidia ones.

---

