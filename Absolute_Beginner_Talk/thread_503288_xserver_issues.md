---
title: "xserver issues"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by zapyourit on 2007-07-17
I installed Ubuntu and tried to change my resolution to 1280x1024 (running an ATI Radeon 9200) by switching to fglrx. However, the actual change of resolution never worked. I used ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and changed over to the fglrx driver. That did not work, leaving my panels with white outlines. So I switched over to the open source ati radeon driver. Yet that did not work and the panels problem remained as well. I rebooted a few minutes ago, and it told me that I had issues with the xserver xorg files of some kind and could not start. (I would code it into here, but I dont know how to copy text from the terminal and post here.) It left me in the terminal, I went back to ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and switched back to the original driver i was using and tried to reboot. However the same problem came up. Any ideas or advice?

---

### Post by zapyourit on 2007-07-17
should i just be reinstalling feisty and not messing with the things i changed?

---

