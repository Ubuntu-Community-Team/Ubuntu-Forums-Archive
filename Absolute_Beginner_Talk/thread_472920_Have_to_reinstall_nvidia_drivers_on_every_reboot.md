---
title: "Have to reinstall nvidia drivers on every reboot"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by gullf1sk on 2007-06-13
Anyone else got this problem? Its getting old :(

---

### Post by bbarcelo on 2007-06-13
How do you know you have to install them on every reboot? i.e. What symptoms is your computer showing that makes you think that is needed? Did you manually install the nvidia drivers or did you just let Ubuntu install them?

---

### Post by lazyart on 2007-06-13
I have a FX5200 and no issues.  I installed```
sudo apt-get install nvidia-glx-new
``` and am good.  I rarely reboot, but when I do there is never a problem.

---

### Post by reidbold on 2007-06-13
I have this problem too. The drivers in the repo aren't up to date, I need the new ones. Installing the drivers from the nvidia site involves rebuilding a part of the driver, so it's a bit length.. Every reboot, gdm crashes because there is no nvidia driver. After installing driver, gdm restarts and everything is good, until the next time you reboot. 

The nvidia module is loaded on boot up.

---

### Post by NewJack on 2007-06-13
I had a problem with 7.04 crashing upon boot for some reason.  After 7 times trying to install the drivers from the repos, I did the following:


Did a clean install of 7.04, then install ENVY immediately after that.  Then I was able to install all of the other updates/programs that I needed after that.  No problems since.

---

