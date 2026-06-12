---
title: "Ubuntu 9.10 + Macbook Pro + Performance"
date: 2009-09-15
forum: Apple Hardware Users
---

### Post by brujoand on 2009-09-15
Hi, 
I just tested the kubuntu 9.10 on a Macbook Pro 5.1 and pretty much, everything works out of the box. Even the touchpad is almost awesome, except for two-finger-dragging which does not work. Now the only thing holding me back from from loosing OSX completely and going back to Linux is the heat ande batteryTime. Since we cant use the low end graphic card (the MBP 5.1 has two) were stuck with a heat problem and a battery drain. 
I have had a couple of threads on this topic earlier and the conclution has been that this can not be achieved without Booting Ubutnu via EFI instead of the Emulated-Bios. But this will leave us without hardware acceleration for the graphic card since there are no NVIDIA-drivers (to my knowledge) that will support EFI for linux. 

Now, I'm just wondering if anybody has come across anything, that can prove me wrong and help fix this annoying situation.

Thanks

---

### Post by bravemenrun333 on 2009-11-02
Any news to this?

Stuck on the same issues.

Thanks

---

### Post by maflynn on 2009-11-02
I can't answer on switching to the 9400m, but search the forums for some scripts to control the fans.  I use those and they keep my MBP pretty cool.  

Here's one of my scripts to set the fan speed to 3500, I use a variety of them, setting them to 3000, 3500, 4000, etc.  I put them in my ~/bin folder and they're accessible from any terminal session.


```

echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan2_min

```

---

### Post by brujoand on 2009-11-02
Yeah thats a good tip, also:

```

sudo cpufreq-set -c 0 -g conservative
sudo cpufreq-set -c 1 -g conservative

```

Will scale the cpu down to a conservative scheduler.

---

