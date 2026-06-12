---
title: "x server failed"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by spectrum48k on 2007-06-24
I used a program called ENVY to install the "correct" NVIDIA driver on my UBUNTU system. Now I can't boot up. All I get is a message to say X server failed to load because I dont have a driver hardware mismatch.  How do I delete the NVIDIA driver and get my Gui back???

Thanks

---

### Post by logos34 on 2007-06-24
> **spectrum48k said:**
> I used a program called ENVY to install the "correct" NVIDIA driver on my UBUNTU system. Now I can't boot up. All I get is a message to say X server failed to load because I dont have a driver hardware mismatch.  How do I delete the NVIDIA driver and get my Gui back???

Thanks

oh, c'mon, you can try harder than that.

Open Envy back up and select "uninstall the Nvidia driver"

---

### Post by bigken on 2007-06-24
sudo dpkg-recofigure -phigh xserver-xorg

---

### Post by logos34 on 2007-06-24
> **bigken said:**
> sudo dpkg-recofigure -phigh xserver-xorg

set it back to 'nv'

---

