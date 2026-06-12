---
title: "/dev/hda1?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by BlueLava on 2006-09-02
Hi!
When I booted up today ,before the login screen came up this message appeared:
/dev/hda1 mounted 30 times without check, check forced
After the check everything carried on as normal. Can anyone tell me what this means, is it something I should check more often and if so how?

---

### Post by meng on 2006-09-02
This is normal. The filesystem is checked regularly every so often, and every 30 times is a reasonable frequency.

---

### Post by BlueLava on 2006-09-02
What is the filesystem being checked for

---

### Post by annda on 2006-09-02
it scans the disk for potential disk errors.

if you want to disable the automatic check because you find it annoying, edit your /etc/fstab entry for hda1 and change the last digit from 1 to 0.

---

### Post by BlueLava on 2006-09-02
I think I will leave it as it is, I just like to know what things are doing.
Thanks guys, for helping me out.

---

