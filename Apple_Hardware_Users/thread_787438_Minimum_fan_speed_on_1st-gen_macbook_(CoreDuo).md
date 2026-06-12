---
title: "Minimum fan speed on 1st-gen macbook (CoreDuo)"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by mrs. respect on 2008-05-08
How can I set the minimum fan speed on my first-generation MacBook? I have tried this
```
sudo echo 3500 > /sys/devices/platform/applesmc.768/fan1_min
```
But I still got "Permission denied." Is there another way I can increase my minimum fan speed?

Also, my macbook isn't Core2Duo, but it is CoreDuo. I only have "fan1" in the applesmc folder and any time I look at my CPU info it only shows info for one core. But I do have two cores, right? Is something wrong?

---

### Post by holr on 2008-09-02
Try running the command as root, rather than with sudo. Although I have a core2duo macbook pro, I can't set the fan speed with sudo, only su.

---

### Post by cyberdork33 on 2008-09-02
> **mrs. respect said:**
> How can I set the minimum fan speed on my first-generation MacBook? I have tried this
```
sudo echo 3500 > /sys/devices/platform/applesmc.768/fan1_min
```But I still got "Permission denied." Is there another way I can increase my minimum fan speed?

See this:
[http://ubuntuforums.org/showthread.php?t=412329](http://ubuntuforums.org/showthread.php?t=412329)

It is not for the same command, but the issue is the same. You should use 'tee' as instructed.

> **mrs. respect said:**
> Also, my macbook isn't Core2Duo, but it is CoreDuo. I only have "fan1" in the applesmc folder and any time I look at my CPU info it only shows info for one core. But I do have two cores, right? Is something wrong?Yes, you should have 2 cores if you have a 'duo'. 

> **holr said:**
> Try running the command as root, rather than with sudo. Although I have a core2duo macbook pro, I can't set the fan speed with sudo, only su.
Thsi is true for the same reason as I above. Use 'tee'.

---

