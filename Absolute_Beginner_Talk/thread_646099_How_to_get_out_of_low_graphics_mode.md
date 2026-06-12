---
title: "How to get out of low graphics mode"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2007-12-20
I'm new to ubuntu but not to linux. So just a quick question: When i installed ubuntu gusty gibbon (7.10) I installed in low graphics mode... How, now that it's installed, do i get out of it?

---

### Post by overdrank on 2007-12-20
> **Mitchlb said:**
> I'm new to ubuntu but not to linux. So just a quick question: When i installed ubuntu gusty gibbon (7.10) I installed in low graphics mode... How, now that it's installed, do i get out of it?

HI and you may check under system, administration restricted drivers to see if you graphics card need the drivers. Also you may reconfigure you xorg with this command ```
sudo dpkg-reconfigure -phigh xerver-xorg
``` Good luck!

---

### Post by Mitchlb on 2007-12-20
Gotcha. Thanx!

---

### Post by CityofAsh on 2007-12-23
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

