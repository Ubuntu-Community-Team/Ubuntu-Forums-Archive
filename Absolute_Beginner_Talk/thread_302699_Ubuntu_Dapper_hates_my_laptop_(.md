---
title: "Ubuntu Dapper hates my laptop :("
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-19
My videos and sound play and x2 the speed as they should, and I get NO sound at all. Yesterday I had the same problem but I fixed it by changing a setting by adding "no_timer_check" here to my  /boot/grub/menu.lst file

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro **no_timer_check**
```

So what now if the problem with my sound/videos?

---

### Post by spamzilla on 2006-11-19
Anyone?

---

