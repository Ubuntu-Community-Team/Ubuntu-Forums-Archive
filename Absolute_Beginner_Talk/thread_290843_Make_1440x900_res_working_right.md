---
title: "Make 1440x900 res working right"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by breezey on 2006-11-01
I just installed Ubuntu 6.06 on my machine using 19" viewsonic widescreen monitor powered by ATI Radeon video card. Installation went smoothly, all devices are recognized and I got an option to choose 1440x900 resolution which is the native resolution of the monitor. The problem is that Ubuntu desktop does not occupy the whole monitor and it shows tiled desktop (the right end and bottom end of the monitor repeats what is on the left and top bottom of the monitor)... I hope you got what I mean here.

Any suggestion on how to solve this problem? Thank you.

---

### Post by raqball on 2006-11-01
have you tried running x config?

---

### Post by breezey on 2006-11-01
hi raqball, thank you for your reply. I am an absolute beginner in Linux so I am not sure how to do that. Is it a command line or can be done through the GUI? Thanks.

---

### Post by raqball on 2006-11-01
In terminal type this

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the steps and select everything as is for now (unless you see something obvious that needs to be changed). It will reconfigure your  monitor and mouse...

---

### Post by breezey on 2006-11-01
Thanks. I will try that. I am not in front of my Linux machine right now. Will update you.

---

### Post by breezey on 2006-11-09
Sorry I just replied. Thank your for your help, it works. Now my Ubuntu displays the correct resolution perfectly. Thanks again.

---

