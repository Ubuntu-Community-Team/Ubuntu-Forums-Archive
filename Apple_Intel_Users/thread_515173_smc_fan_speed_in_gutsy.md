---
title: "smc fan speed in gutsy"
date: 2007-08-01
forum: Apple Intel Users
---

### Post by anujseth on 2007-08-01
any idea how to set the minimum fan speed in gutsy tribe 3 .... echo 3000 > .... in /etc/init.d/acpid does not work ... the only option is to boot into OS X first use smcfan control set your speed and restart and go to ubuntu ... anybody know of a better way ?

---

### Post by cyberdork33 on 2007-08-01
> **anujseth said:**
> any idea how to set the minimum fan speed in gutsy tribe 3 .... echo 3000 > .... in /etc/init.d/acpid does not work ... the only option is to boot into OS X first use smcfan control set your speed and restart and go to ubuntu ... anybody know of a better way ?

The mactel patches for 2.6.22 include applesmc which (I thought) was supposed to be able to control fan speed. I don't know how one would do that manually though.

---

### Post by kainrcir on 2007-08-03
Try this (path may not be exactly right;  currently using 2.6.22-9):

sudo modprobe applesmc
sudo sh -c "echo 3000 > /sys/devices/platform/applesmc.768/fan1_min"

---

### Post by anujseth on 2007-08-03
oh man!!! i just formatted i dont have ubuntu right now ... can any one confirm if this works with tribe 3 ...

---

### Post by anujseth on 2007-08-04
it works perfectly ... thanks a pile

---

### Post by jamesotron on 2007-09-23
I'm using Gutsy on my first revision MacBook Pro.  applesmc works perfectly, but I had to do:

echo 1 > fan1_manual
echo 1 > fan2_manual
echo 3000 > fan1_output
echo 3000 > fan2_output

in order to get fans to go faster than 1000rpm (the default).  Does anyone know if there's a way to make applesmc more aggressive at controlling the cpu temperature?

---

