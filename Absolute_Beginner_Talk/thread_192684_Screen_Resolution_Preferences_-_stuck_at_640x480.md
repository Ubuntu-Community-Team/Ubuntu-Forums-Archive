---
title: "Screen Resolution Preferences - stuck at 640x480"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-09
Hi,

How do I enable all screen resolutions? ubuntu has gone with 640x480 and there is no option to change this in Screen Resolution Preferences.

I am looking at xorg.conf but can't see the problem.

Thanks.

---

### Post by _simon_ on 2006-06-09
this should help you out:

[https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29](https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28resolution%29)

---

### Post by CameronCalver on 2006-06-09
That happened to me to go to synaptic then search for automatix download it then go applications system automatix download nvidia drivers then after its finished restart your comp and then write back if it work or not

---

### Post by u.b.u.n.t.u on 2006-06-09
Thanks _simon_ and CameronCalver.

I managed to fix the problem by doing the following:

1. ```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

2. ```
sudo nvidia-xconfig
```

3. reboot

---

### Post by CameronCalver on 2006-06-09
well when you install automatix and install nvidia drivers it actually installs those 3 thing so its the same thing lol and thats alright i like helping others

---

