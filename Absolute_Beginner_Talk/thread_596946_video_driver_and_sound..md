---
title: "video driver and sound."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by liem_nguyenho on 2007-10-30
i just installed Ubuntu 7.04, but i don't know how to install driver for NVIDIA GForce 7300 and sound card.
Can anybody help me, please ? 
I appreciate that.

---

### Post by MrFSL on 2007-10-30
From the top toolbar click:

System > Administration > Restricted Drivers Manager

From here you should be able to install a driver for the nvidia.

As far as the audio... what audio card/chip do you have?

You might want to try:
```
lspci | grep -i audio
```

---

### Post by kennedyjch on 2007-10-30
I have successfully installed my Nvidia-based graphics card on 7.04 using ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)). Follow the instructions - it's terribly simple.

For 7.10 worked out of the box - needed to use restricted drivers for 3D stuff - directly supported by installing the proprietary drivers and rebooting.

---

