---
title: "Ubuntu Running in Low-Graphics Mode After Reboot"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by undoIT on 2010-05-01
I keep getting a warning messaged almost every time I reboot about Ubuntu running in low-graphics mode on a Macbook 5,1. This has been happening since Lucid Beta 1.

> Failed to initialize the NVIDIA kernel module. Please see the
system's kernel log for additional error messages and
consult the NVIDIA README for details.
*** Aborting ***
Screen(s) found, but none have a usable configuration.

After I finish loading in low graphics mode I have to run "sudo nvidia-xconfig". Then, the next reboot the graphics card driver is loaded properly. Is anyone else experiencing this problem or have an idea how to correct it? I know it is a long shot, but do you think doing a fresh install of the stable release would work?

---

### Post by alexmurray on 2010-05-01
I get the same thing - i think what is happening is that X is starting before the nvidia driver has fully loaded and initialized the GPU - instead what I do is exit to a login console, then login and manually start up gdm:
```

sudo service gdm start

```

which seems to do the trick that way you don't have to reboot.

See this bug report on Launchpad too: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436)

---

### Post by undoIT on 2010-05-01
> **alexmurray said:**
> I get the same thing - i think what is happening is that X is starting before the nvidia driver has fully loaded and initialized the GPU

Thanks, that was my hunch. I'll try what you recommended next time I reboot. Way better than what I've been doing :P

---

### Post by sventek on 2010-05-01
I had the same issue with an NVIDIA card and I discovered that the manufacturer provides the necessary software written for linux.  ONce I started using the NVIDIA drivers and software the problem went away.

---

