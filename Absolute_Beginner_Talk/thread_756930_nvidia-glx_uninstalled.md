---
title: "nvidia-glx uninstalled"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by toddpedlar on 2008-04-16
I am trying desperately to get my x11 working after nvidia-glx was uninstalled by synaptic package manager.  If someone can tell me why this would be done, I would appreciate it. I'm still quite perturbed by this because this whole thing has wasted (so far) about a day's work.

I can boot the machine fine with the LiveCD - it happily works, synching to our network, etc.
Graphics look totally great, etc.

When i do a "normal boot" i get no X, because the nvidia-glx drivers aren't there.  I can't
seem to get networking running from the command line, so I can't apt-get install nvidia-glx (which I assume would fix everything).  I don't know how to get source from the CD when I"m on the command line, but I suppose that would be possible.  (How do I do that?) 

Also - when I boot normally and fail to get the X server going, the log file with the problems listed in it says "Failed to load module "nvidia" (module does not exist, 0)"  and then "No drivers available"

I don't know if that helps but that's how it is.  Please suggest anything that might help.  I'm really sitting idle here and not happy about it.

---

### Post by aktiwers on 2008-04-16
Why don't you go download the Nvidia driver from there webpage using the liveCD.

[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

Then save it on your harddrive, like in your users home folder (not livecd home folder but your own homefolder).

Then reboot and boot into Terminal.

Then type:

```
sudo /etc/init.d/gdm stop
``````
sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```And then
```
sudo ./NVIDIA-Linux-x86-169.12.pkg1.run
```After that reboot
```
sudo reboot
```

Then your driver should be installed.

---

