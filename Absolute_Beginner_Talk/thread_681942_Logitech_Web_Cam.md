---
title: "Logitech Web Cam"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-29
Is there a software for ubuntu that works with this web cam? screen shot below of the information to the one that i have.

---

### Post by benfindlay on 2008-01-29
there are good packages for generic drivers for webcams such as > spca5xx-source
If you already own it you can type ```
lsusb
``` when it is plugged in to find out the hardware code which will look something like > 2500:720c
A quick google search for this specific code with the word "linux" or "ubuntu" will show you whether there are any proper drivers available.

Hope this helps!

---

### Post by linuxwizard on 2008-01-29
That webcam should just work by plugging it in no need to add driver. For appls. to use it in look at Ekiga, Camorama, Cheese.

---

