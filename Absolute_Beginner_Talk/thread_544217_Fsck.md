---
title: "Fsck"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-09-06
Just trying to get to grips with managing the file system check.   Have I got this right ...?

That Autofsck does not do more than make it very convenient to change the checking from the boot up to shut down (so that it may be unattended) and that there is no configuration script where changes may be made?

and ...

That to change the frequency that drives are checked you use the tune2fs command with a syntax similar to the following and there is no application with a gui to make this a more fun event to play with?
sudo tune2fs -c xx /dev/drivename
(where xx is the number of boot events before check)
It seems that you need to repeat this command for every hard drive you have on your system.

---

### Post by be4truth on 2007-09-06
Do not run this on a mounted file system.

```
sudo tune2fs -c xx /dev/drivename
```

---

### Post by expatCM on 2007-09-06
good comment ..... thank you :)

---

