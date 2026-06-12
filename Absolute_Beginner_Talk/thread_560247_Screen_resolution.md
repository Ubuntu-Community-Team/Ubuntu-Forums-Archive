---
title: "Screen resolution"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-09-26
Hi, i have a 17" wide screen, screen on my laptop (1440x900) but in the screen resolution thing in Ubuntu can I only choose 
1280x800
1280x768
1152x768
1024x768
800x600
640x480
But I wan't 1440x900...how?

---

### Post by Kobalt on 2007-09-26
Open up a terminal and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the **spacebar** and then validate with Enter. Finally restart X with Ctrl+Atl+Backspace, and you should be done.

---

### Post by skyjacker on 2007-09-27
> **Kobalt said:**
> Open up a terminal and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the **spacebar** and then validate with Enter. Finally restart X with Ctrl+Atl+Backspace, and you should be done.

Thank you - Thank you:) I have been trying for three weeks to get a 1440x900 resolution on my 19" widescreen monitor. No one told me how to select the resolutions I wanted when I edited Xserver. My problem is solved.

---

