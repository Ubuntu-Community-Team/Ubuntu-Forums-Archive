---
title: "nvidia_bl"
date: 2009-11-24
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2009-11-24
Hi. 

I have a MacBook Pro 5.1 with Karmic. In my /etc/modules I have the nvidia_bl that I think is used to control backlight. But even if I remove the nvidia_bl from /etc/modules I can control the backlight using fn+f1/f2 and it works more gradually and more close to the gauge. 

My questions are: 
1. nvidia_bl, what is it? I googled around and I didn't find an satisfactory explanation. 
2. Should I still use it with Karmic and my Mac 5.1 ?

I've upgraded from Jaunty to Karmic; if you see something wrong, please tell me:
```

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
coretemp
applesmc
bcm5974
usbhid
nvidia_bl 

```

---

### Post by _mario_ on 2009-11-25
> **luigi.viggiano said:**
> 
I have a MacBook Pro 5.1 with Karmic. In my /etc/modules I have the nvidia_bl that I think is used to control backlight. But even if I remove the nvidia_bl from /etc/modules I can control the backlight using fn+f1/f2 and it works more gradually and more close to the gauge. 

My questions are: 
1. nvidia_bl, what is it? I googled around and I didn't find an satisfactory explanation.


nvidia_bl is a kernel-level driver that allows user-level applications (e.g. gnome-power-manager) to adjust screen backlight. basically, this is the same functionality as the mbp_nvidia_bl driver provides, with some subtle differences:
[LIST=1]
[*] Interface: nvidia_bl drives the **Nvidia graphics adapter**'s smartdimmer registers directly, which allows a more fine-grained control (1024 levels). It is not limited to Apple machines, but Nvidia graphics adapters.

mbp_nvidia_bl, in contrast, uses a firmware interface present on recent **Apple machines**, that only provides 16 distinct levels. This is what Apple's bootcamp Windows drivers use as well. Having only 16 levels is most annoying in dark environments where 1024/16=64 is still too bright (I prefer to go down to 20, which also safes power). Despite it's name mbp_nvidia_bl also supports some Apple machines with Intel graphics chips, i.e. MacBook Air 1.

[*] Loading: nvidia_bl cannot be loaded automatically by the kernel. That's why you have to put this line to /etc/modules. mbp_nvidia_bl will be loaded automatically, if a suitable device is present. You can check this by running:
```

lsmod | grep nvidia_bl

```

[*] Support: In theory both should work, but in practice on some machines the drivers fail, e.g. mbp_nvidia_bl on MacBook 5 / MacBook Air 2 (Geforce 9400M). Symptoms: Changing brightness simply does have no effect.
[/LIST]

> **luigi.viggiano said:**
> 
2. Should I still use it with Karmic and my Mac 5.1?


Use whatever you like. I'd prefer nvidia_bl over mbl_nvidia_bl, if it works on your machine ;-)

Please also note: These drivers only provide a sysfs-interface for user-level applications. If both drivers are loaded it's not exactly clear which one gets used (by gnome-power-manager). I addition, pommed (if you use it) uses the sysfs-interface and falls back to a built-in driver otherwise. In case of machines with Nvidia graphics adapter, this is the same firmware interface mbp_nvidia_bl uses.

> **luigi.viggiano said:**
> 
```

bcm5974
usbhid

```

Why are you loading bcm5974 and usbhid manually? Doesn't your trackpad work out of the box?

ciao,
Mario

---

