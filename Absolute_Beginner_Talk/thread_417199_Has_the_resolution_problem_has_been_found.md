---
title: "Has the resolution problem has been found?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by arya6000 on 2007-04-21
Hello

I have a problem with my resolution, its stock at 800X600. In Edgy I used to be able to use 1024X768. I tried installing the Nvidia driver in many diffrent ways but it was the same thing. Is there anything that I can do?

Thanks

---

### Post by Medieval_Creations on 2007-04-21
Here's a couple things to try.  It usually works.

sudo apt-get install nvidia-glx  #ensures that we have the newest drivers installed
sudo dpkg-reconfigure xserver-xorg  #allows you to choose the nvidia driver and resolutions

Then restart X.

---

### Post by arya6000 on 2007-04-21
unfortunately it didn't work. Could this be a bug?

---

### Post by Medieval_Creations on 2007-04-21
EDIT: [duplicate post]

---

### Post by Medieval_Creations on 2007-04-21
Anything is possible.  Some hardware is always buggy.

What vid card do you have.  We might need to try the nvidia-legacy drivers instead.

---

### Post by arya6000 on 2007-04-21
> **Medieval_Creations said:**
> Anything is possible.  Some hardware is always buggy.

What vid card do you have.  We might need to try the nvidia-legacy drivers instead.

I checked to see if I'm using the right driver, and I was I have a Geforce 3 Graphics card

---

