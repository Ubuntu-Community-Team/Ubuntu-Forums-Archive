---
title: "nvidia-glx-config"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-02-08
Hi,

By typing ```
sudo nvidia-glx-config enable
```
I get: > Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

What is wrong?

---

### Post by renzokuken on 2007-02-08
well i guess the first question is.......have you actually installed the nvidia driver?

---

### Post by steve.horsley on 2007-02-08
> **renzokuken said:**
> well i guess the first question is.......have you actually installed the nvidia driver?

To find out, System->Administration->Synaptic and search for package **nvidia-glx**.

---

### Post by neighborlee on 2007-02-10
> **steve.horsley said:**
> To find out, System->Administration->Synaptic and search for package **nvidia-glx**.

I am having the same problem, and yes nvidia-glx is installed.

cheers
nl

---

### Post by Perfect Storm on 2007-02-10
If the driver is install, you might try setting it manually;
```
sudo nano  /etc/X11/xorg.conf
```

Go to the Section "Device" and change driver "nv" to "nvidia"

Restart X.

If it fails you can easely change "nvidia" back to "nv".

---

