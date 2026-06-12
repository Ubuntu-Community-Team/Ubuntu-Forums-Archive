---
title: "macbook pro 7,1 not shutting down without holding power button"
date: 2013-03-20
forum: Apple Hardware Users
---

### Post by fourdigit on 2013-03-20
Using the 64 bit desktop version of Ubuntu 12.10, it won't shutdown or reboot properly without holding down the power button. It will only go to a blank screen and then hang there forever. running "sudo shutdown -h now" has the same results. The documentation for Lucid offers this advice: help.ubuntu.com/community/MacBookPro7-1/Lucid#Reboot which, unfortunately, changed nothing.

---

### Post by fourdigit on 2013-03-20
As it turns out, the driver for the nvidia graphics card was causing this, however I don't know why. I was using the nvidia-current driver, as the guide [here]("https://help.ubuntu.com/community/MacBookPro7-1/Quantal#Activate_proprietary_nvidia_driver") told me to do.

**The solution:** change the driver the graphics card is using.
* Software Sources > Additional Drivers > *and change the nvidia driver to nvidia-experimental-304

**FAIL to reboot/shutdown:**
[LIST]
[*]    nvidia-current
[*]    nvidia-current-updates
[*]    nvidia-experimental-310
[/LIST]
**Able to reboot/shutdown:**
[LIST]
[*]    nvidia-experimental-304
[*]    nouveau(but with other graphics related issues)
[/LIST]
[SIZE=6]
I would appreciate it if anyone could confirm this, as I am only able to replicate it on my own machine.[/SIZE]

---

