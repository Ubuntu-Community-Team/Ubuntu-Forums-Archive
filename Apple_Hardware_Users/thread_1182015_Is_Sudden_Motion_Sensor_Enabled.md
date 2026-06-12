---
title: "Is Sudden Motion Sensor Enabled?"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by NoBugs! on 2009-06-08
Does anyone know if this hard drive protection is enabled in Ubuntu 9.04?
[http://support.apple.com/kb/HT1934](http://support.apple.com/kb/HT1934)
Does it require extra setup?

---

### Post by s3MA00RRNY on 2009-06-08
My extremely uneducated guess would be if the OS does not explicitly disable it, it will be enabled. That's how hardware usually works. Just like if the OS does not handle throttling the CPU, it will constantly run at full speed (Unless the CPU overheats, of course).

---

### Post by NoBugs! on 2009-06-08
According to [this]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Motion%20Sensor"), it won't work in linux. Maybe because Macbook is using a different system, not hdaps?

---

### Post by cyberdork33 on 2009-06-08
the sudden motion sensor is enabled with the applesmc driver... now whether it actually does anything is a different story.

---

### Post by NoBugs! on 2009-06-09
According to [this]("http://kernelnewbies.org/Linux_2_6_28#head-3ac72425f262922b92d6b53c79b84f2c44d00c2b"), kernel 2.6.28 has built-in hard disk protection, so does that mean it is working in Jaunty?

---

### Post by rCXer on 2009-06-09
No. All it it means is that the kernel can park the hard drive head. Extra software is needed to gather data from the laptop's motion sensors.  A program called [hdapsd](http://www.thinkwiki.org/wiki/HDAPS) has been written to do this IBM/Lenovo laptops. I don't know if anyone has done this for a Mac but you can write one if you want to ;)

---

### Post by barbaGNU on 2009-06-13
it's simple, you must recompile your kernel  enabling this module

---

### Post by NoBugs! on 2009-06-13
> **barbaGNU said:**
> it's simple, you must recompile your kernel  enabling this module

What module? The latest applesmc?

There is a file in /sys/devices/platform/applesmc.768/position that seems to have motion sensor data in 3 numbers. On a stable surface this file has something like "(-5,18,277)"
It looks like these are numbers from the side-to-side sensor, tilt back/forward sensor, and up/down acceleration?

---

### Post by barbaGNU on 2009-06-14
```
CONFIG_SENSORS_AMS=m
CONFIG_SENSORS_AMS_PMU=y
CONFIG_SENSORS_AMS_I2C=y
```

---

### Post by NoBugs! on 2009-07-02
> **barbaGNU said:**
> ```
CONFIG_SENSORS_AMS=m
CONFIG_SENSORS_AMS_PMU=y
CONFIG_SENSORS_AMS_I2C=y
```

Is that a command? A config file? Something to add to a config file?

---

### Post by Rog-Mahal on 2009-07-03
Those are options you will need to enable when compiling a kernel from source. You won't be able to enable them without recompiling, AFAIK.

---

### Post by NoBugs! on 2009-07-06
Why isn't it enabled by default, could it possibly cause problems?
Is there a kernel .deb package somewhere with this configuration?

---

### Post by NoBugs! on 2009-11-02
Can this hard drive protection be enabled in 9.10? in 10.04?
Will it be enabled by default?

---

