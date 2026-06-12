---
title: "Resolution Problems in Edgy Eft"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Lunias on 2006-11-16
Hello, I just installed Ubuntu 6.10. I installed the nvidia driver 1.0-9629 for my geforce 7900gtx. I have a widescreen monitor with native resolution of 1680x1050, but when I go to change it in the nvidia x server settings or try to add it directly to the x config file I get an "out of range" display on my monitor. This is odd because I have been running this resolution with no problems in windows xp. I am sure that I am missing something. Thanks in advance.

-Lunias

---

### Post by emuman on 2006-11-16
Try to detect your display with nvidia-settings. Can you select the 1680x1050 resolution with this tool?

---

### Post by Lunias on 2006-11-16
I can select that resolution with the nvidia tool, but if I hit apply 1 of 2 things happens.

1. if refresh rate is set to auto it goes out of range.
2. if refresh rate is set to 60 the graphics block up, I cannot click and sometimes cannot see anything at all, but glitched boxes. I usually have to restart gdm.

---

