---
title: "Upgrading problem"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2007-10-14
I recently upgraded Feisty to Gutsy. Everything seemed fine except when I boot I get a screen which lets me select my video card and monitor. I to select both and click on ok  it reboots and to avail I get the same screen. Has anyone had this problem? If so I would appreciate your input and help.

---

### Post by Abild on 2007-10-14
Try running
sudo dpkg-reconfigure -phigh xserver-xorg
and see what happens.

---

