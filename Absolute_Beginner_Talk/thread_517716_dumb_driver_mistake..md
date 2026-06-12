---
title: "dumb driver mistake."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Johnny p on 2007-08-04
I unabled my Nvidia driver (stupidly) and when i restarted ubuntu did not load and it said something like, unable to load X server. all i can do is terminal commands, any idea what i can do to fix my ubuntu? thank you.

---

### Post by overdrank on 2007-08-04
> **Johnny p said:**
> I unabled my Nvidia driver (stupidly) and when i restarted ubuntu did not load and it said something like, unable to load X server. all i can do is terminal commands, any idea what i can do to fix my ubuntu? thank you.

Hi you can use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And answer the questions and hopefully this gets you back to the desktop

---

### Post by 67GTA on 2007-08-04
What driver were you using? There are three for Nvidia. nvidia-glx, nvidia-glx-legacy, and nvidia-glx-new. You can boot into recovery mode at the grub menu, log in, and "sudo apt-get install your_driver". I use ATI, so I'm not sure. Maybe post your Nvidia card model and someone can tell you which one you need.

---

### Post by Aurdal on 2007-08-04
Try running "sudo nvidia-glx-config enable". :)

---

### Post by Johnny p on 2007-08-04
sudo dpkg-reconfigure -phigh xserver-xorg
 That worked! then i installed the driver with Envy and im back, woooo. thank you so much. was about to pull the ubuntu installation cd out =o!

---

### Post by overdrank on 2007-08-04
> **Johnny p said:**
> sudo dpkg-reconfigure -phigh xserver-xorg
 That worked! then i installed the driver with Envy and im back, woooo. thank you so much. was about to pull the ubuntu installation cd out =o!

Glad to hear and good luck! :guitar:

---

