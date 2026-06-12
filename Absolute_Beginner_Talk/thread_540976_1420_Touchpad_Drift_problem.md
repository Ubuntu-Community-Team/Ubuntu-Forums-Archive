---
title: "1420 Touchpad Drift problem"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by garrowolf on 2007-09-02
I have an Inspiron 1420 from Dell with Feisty Fawn on it. My cursor keeps slowly drifting to the top left. I have gone through several fixes that I have found with the xorg.conf file and I haven't been able to solve the problem. 

I found one that sort of worked as a part of another solution. Basically I have to type:

sudo rmmod psmouse
sudo modprobe psmouse

every time I restart my computer. 

Anyone have any idea why this is occurring?

---

