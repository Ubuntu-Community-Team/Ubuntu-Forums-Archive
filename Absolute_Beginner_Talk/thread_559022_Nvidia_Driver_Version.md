---
title: "Nvidia Driver Version"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-09-24
What NVIDIA Driver should i install ? Im running Ubuntu Feisty Fawn 7.04 with a NVIDIA GeForce 5900... Is it okay if i install "NVIDIA-FreeBSD-x86-100.14.11" ?

---

### Post by w4ett on 2007-09-24
Why not use the restricted driver manager.  This will install the correct restricted driver for you.

System>Adminstration>Restricted Driver Manager

---

### Post by ThRixXx on 2007-09-24
I want the newest one :D

---

### Post by g2g591 on 2007-09-24
You would want the [linux driver]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html"). BSD drivers arn't compatible with linux as far as I know.

---

### Post by w4ett on 2007-09-24
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

