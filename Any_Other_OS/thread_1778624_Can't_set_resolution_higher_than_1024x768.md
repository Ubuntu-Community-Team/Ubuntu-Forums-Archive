---
title: "Can't set resolution higher than 1024x768"
date: 2011-06-09
forum: Any Other OS
---

### Post by Mr_VeRiTy on 2011-06-09
Hi, I just got a new pc, and have just done a clean install of linux mint katya, which works fine except it won't let me change the resolution to anything higher than 1042x768, it's supposed to be 1440x900. I have a Nividia graphics card and I've installed the proprietary Nividia drivers. The resolution is fine on a different computer with the same monitor. My sister has the same problem with her resolution except she's using onboard laptop graphics.

I'm not entirely sure what graphics card I have but sudo lshw says:
```
  *-display
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fc000000-fdffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:ec00(size=128) memory:fe980000-fe9fffff
           
```

Does anybody know what's wrong? 1024x768 looks HORRIBLE on this monitor. :C

---

### Post by Grenage on 2011-06-09
Try adding the monitors frequency ranges in your xorg.conf; I have a rough guide [here]("http://www.grenage.com/xorg.html").  You could also try adding the modes with [xrandr]("https://wiki.archlinux.org/index.php/Xrandr"), to see if that helps.

---

### Post by Mr_VeRiTy on 2011-06-09
> **Grenage said:**
> Try adding the monitors frequency ranges in your xorg.conf; I have a rough guide [here]("http://www.grenage.com/xorg.html").  You could also try adding the modes with [xrandr]("https://wiki.archlinux.org/index.php/Xrandr"), to see if that helps.

I tried but that didn't work, BUT when I restarted I noticed that the resolution is FINE on the login screen, but it messes up when I login, it's also fine when I run the LiveCD. I looked in Hardware Drivers, and it says that I installed the Nvidia drivers but am not currently using them, how do I enable them?

---

### Post by Grenage on 2011-06-09
Under *Additional Drivers*, you should get a list of drivers, including a 'recommended' option.  You can enable them there, and they should be used once X has restarted (just reboot).

Once done, you can install nvidia-settings via either Synaptic or the terminal. That should give you some fine control over your display:

```
sudo apt-get-install nvidia-settings
```

---

### Post by Mr_VeRiTy on 2011-06-09
> **Grenage said:**
> Under *Additional Drivers*, you should get a list of drivers, including a 'recommended' option.  You can enable them there, and they should be used once X has restarted (just reboot).

Once done, you can install nvidia-settings via either Synaptic or the terminal. That should give you some fine control over your display:

```
sudo apt-get-install nvidia-settings
```

I  had already done the part about Additional Drivers, but it didn't enable them when I clicked enable, however the nvidia settings thing allowed me to change my resolution properly, thanks!

---

### Post by Grenage on 2011-06-09
Outstanding, glad to hear it.

---

