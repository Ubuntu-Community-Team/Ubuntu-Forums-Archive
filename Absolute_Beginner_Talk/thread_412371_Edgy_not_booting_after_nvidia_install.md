---
title: "Edgy not booting after nvidia install"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by saxonjf on 2007-04-18
So I installed an Nvidia GeForce MX 4000 on Windows, all looks good so far there.

However, when I try to boot Edgy, the boot screen with the yellow bar comes up, but halfway across,  it drops off, and the check screen is forced.

At about 58%, the check screen fails, goes over some failed items, and creates a root shell, and I have no idea what to do.

Is there a way to install the driver from a root shell so I can boot Edgy (and then upgrade to Feisty on the 19th)?

I hate having to do all this from Windows, but I don't know what else to do.

---

### Post by Perfect Storm on 2007-04-18
In failsafe;
```
sudo aptitude install nvidia-glx
sudo dpkg-reconfigure -phigh xserver-xorg
startx

```

---

### Post by saxonjf on 2007-04-18
What's failsafe?

---

### Post by Perfect Storm on 2007-04-18
After the BIOS, you'll see a countdown before booting into Ubuntu, hit [esc]



But I have a feeling it's not a driver issue but try anyway.

---

### Post by saxonjf on 2007-04-18
When I hit [esc] at the countdown, it just stopped the countdown.

When I tried booting a different version of Ubuuntu (amongst the other Ubuntu choices, and it lloke like 6.06), it showed what it was attempting, and it showed a fail for loading drivers.

I don't know how to roll back a driver in windows, wouldn't know how to get the old driver back...

---

### Post by Perfect Storm on 2007-04-18
Okay try boot up normally, when it jump to CLI, type in the commands I shown.

---

