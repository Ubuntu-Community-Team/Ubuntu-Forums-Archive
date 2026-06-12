---
title: "[SOLVED] Wine and the USB ports"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-11-08
I have a Garmin Legend CX GPS toy and I have some maps from Garmin to go with it. Now, I don't know how to make the unit be seen to the Garmin mapsource software. It's a USB device and the Garmin software says it doesn't see it.

Cheers,
Sidd

---

### Post by finer recliner on 2007-11-08
first check if ubuntu correctly sees your USB thing. type this command at a terminal:

```

lsusb

```

this will list everything plugged into your USB ports.

---

### Post by siddartha on 2007-11-08
Yes, it sees it and it can communicate with it, but only one way (from device to pc).

---

### Post by siddartha on 2007-11-17
There seems to be no USB support right now in Wine unless you get some sort of USB-> serial driver converter. This means the USB 'thingie' has to be Linux kernel supported.

In my case with the Garmin GPS I have a kernel module called just like this garmin_gps which loads up by default in Ubuntu and makes the Garmin software work with a com port.

Cheers,
Sidd

---

