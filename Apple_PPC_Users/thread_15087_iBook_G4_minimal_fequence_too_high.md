---
title: "iBook G4 minimal fequence too high"
date: 2005-02-11
forum: Apple PPC Users
---

### Post by Laf on 2005-02-11
Hi,

On my iBook G4, the minimal frequence is 50% of total, not 20 or less... is it normal ?

It causes two problems :

- The "wind" inside the computer runs quite often and is noisy.
- The autonomy is bad, about 3 hours (istead of 5 or 6 on MacOSX).

My CPU is a 1.2Ghz.

If i do : **$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq** it tells me : **599999**.

I would like it really lower, about 20% of highest possibility...

I tried : **sudo echo 199999 /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq** but it does nothing.

I also tried kernel 2.6.8 from Warty (the default one after installation) and the 2.6.11 from Hoary. Both PowerPC build.

Informations that can help :

```
$ cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 599MHz
revision        : 1.1 (pvr 8003 0101)
bogomips        : 598.01
machine         : PowerBook6,5
motherboard     : PowerBook6,5 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001a
L2 cache        : 512K unified
memory          : 256MB
pmac-generation : NewWorld
```

---

### Post by toojays on 2005-02-12
Sorry, but on the 7447A, power management can only go at full-speed or half-speed.

There a possibility to kind of "fake" running at lower speeds, but nobody has written a driver to do it. I don't think Apple does this either. Presumably the power savings are not worth the effort.

Other things to look into with respect to battery consumption is to enable hard drive power management features, and to use the "DynamicClocks" option in the radeon driver of Xorg.

I wish I knew a quick way to measure whether a particular power saving option is doing any good.

---

### Post by Laf on 2005-02-14
As you said i added DynamicClocks option in my "/etc/X11/xorg.conf" :

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9+ (RV250)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
        Option          "DynamicClocks"         "on"
EndSection

```

Nothing seems to change, i look at the battery and it's always so weak : 3h30 for 91%.

How to enable the harddrive powersave ?

Thanks in advance.

---

