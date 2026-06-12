---
title: "[SOLVED] Monitor Hz level"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-01-30
Hello,

In my screen resolution i only have the capability to select between 50 and 51 Hz 
I have a LG 22" lcd and used to run it 75 hz is there somthing i can change to solve this problem.

Thanks

---

### Post by FuturePilot on 2008-01-30
What is your graphics card? Did you install a restricted driver for it?

---

### Post by cane1832 on 2008-01-30
I have the nvidia 7950 card and the driver not to sure how to find that

---

### Post by FuturePilot on 2008-01-30
Try System>Administration>Restricted Driver Manager.

---

### Post by cane1832 on 2008-01-30
It says i have NVIDIA accelerated graphics driver (latest cards)

---

### Post by FuturePilot on 2008-01-30
Don't pay attention to what System>Preferences>Screen Resolution says. It doesn't report the correct refresh rates with the Nvidia driver. Instead try
```
nvidia-settings
```
to adjust the refresh rates.

---

