---
title: "driver for NV Geforce FX 5200"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by oct03 on 2006-10-08
hi,

can anyone tell me where to get the driver for the video card of type Nvidia Geforce FX 5200, because after intallation I only have a resolution of 1024 x 768, but I know that it can more, under ms windows it can up to 1280 x 1024

Thanks in advance.

---

### Post by Max Luebbe on 2006-10-08
Have you installed the nvidia-glx package?
Go into synaptic, download it and follow the instructions that are visible when the package is selected.

If that doesn't work edit /etc/X11/xorg.conf and add the resolution you need. It should be obvious how to do this by looking for other resolutions and then adding the one you need.

Make sure you backup your xorg.conf before you do this, just in case.

Hope this helps.

---

### Post by loell on 2006-10-08
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29")

try the instructions in method 1

---

