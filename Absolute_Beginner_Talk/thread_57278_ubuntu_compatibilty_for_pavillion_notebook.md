---
title: "ubuntu compatibilty for pavillion notebook"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by md4life on 2005-08-15
i just got a hp pavillion zv5000 notebook; its a amd64bit chip processor, with 6m nvidia graphic card, and a broadcom 802.11b/g wireless adpater.  is ubuntu compatiable with my computer, and if so which version?  any help would be  much appreciated.

---

### Post by nocturn on 2005-08-16
> **md4life]i just got a hp pavillion zv5000 notebook said:**
> 

I have a zv5474EA (also AMD64) running 32-bit Hoary.

It works rather well except some issues
- backlight never turns off, even with DPMS enabled
- Suspend or Hibernate do not work (shuts down, but does not resume)
- Cardreader does not work.

All other things are working great.  For the Nvidia driver, you may need this:

[quote]
(Well, actually, the only thing I added there was the IgnoreEDID parameter. Also I added the following to /etc/modprobe.d/nvidia-kernel-nkc (you can add it to whatever file in that folder begins with nvidia).

options nvidia NVreg_Mobile=0


---

