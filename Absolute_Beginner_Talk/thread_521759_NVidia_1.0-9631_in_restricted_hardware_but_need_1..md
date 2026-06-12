---
title: "NVidia 1.0-9631 in restricted hardware but need 1.0-9755"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Olnex on 2007-08-09
My video card is nvidia geforce go 7400 which in the nvidia driver list corresponding to 1.0-9755 driver, so after install ubuntu, I mannually installed 1.0-9755 driver using synaptic(nvidia-glx-new), I rebooted, but the restricted hardware still says i haven't installed the nvidia driver, I enabled it, it download nvidia-glx (without new) which is the 1.0-9631 driver, then I reboot, the system crashed, screen shows:
API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.0-9631, so I changed back to the previous nvidia-glx-new's xorg.conf, but it seems like no nvidia drivers are installed and the restricted hardware still has nvidia driver not enabled, so what can I do to make ubuntu "recognise" nvidia-new?
thanks in advance

---

### Post by MenZa on 2007-08-09
Ahh, I've had this problem a lot lately; fear not!

First of all, ensure you haven't got nvidia-glx or nvidia-glx-legacy installed:

```
sudo aptitude remove nvidia-glx nvidia-glx-legacy
```

Possibly one-by-one, so you're sure they really are gone (I'm not sure how aptitude reacts when one package is installled and another isn't).

The next step is to download the nvidia-glx-new drivers and linux-restricted-modules-generic and linux-restricted-modules-common:

```
sudo apt-get install nvidia-glx-new linux-restricted-modules-common linux-restricted-modules-generic
```

Again, maybe you have to do these individually.

Once you've done this, ensure that the driver in xorg.conf is set to 'nvidia'. Next up, probing the kernel module:

```
sudo modprobe -r nvidia && sudo lrm-manager && sudo modprobe nvidia
```

And then..

```
sudo /etc/init.d/gdm restart
```

Voila! Everything should work. If not, post here again.

---

### Post by Olnex on 2007-08-09
Thanks a lot, I'll try it when I back home.

---

### Post by eznet on 2007-08-12
You Rule!  I am bookmarking this one.. I wound up stumbling here searching for the solution to my nVidia-glx problem and this did it!

I am running Gutsy Gibbon 64Bit Tribe 4 on my Core2Duo dv6000t notebook.  Aside from the 'too be expected' bugs, I am diggin it!

Thanks again!

---

### Post by MenZa on 2007-08-13
> **eznet said:**
> You Rule!  I am bookmarking this one.. I wound up stumbling here searching for the solution to my nVidia-glx problem and this did it!

I am running Gutsy Gibbon 64Bit Tribe 4 on my Core2Duo dv6000t notebook.  Aside from the 'too be expected' bugs, I am diggin it!

Thanks again!

Great to hear this worked for you :)

---

### Post by PresidentJFJ on 2007-08-17
Sorry but that didn't work for me. I don't get the API mismatch anymore. Now I get a different problem. Some problem with reading directories I believe.

---

