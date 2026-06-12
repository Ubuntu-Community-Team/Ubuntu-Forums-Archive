---
title: "Nvidia driver bust"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by chucklechops on 2007-01-19
Ok, this got no replies in the graphics forum so  I'll try in here...

My nvidia driver suddenly fails to load, presumably as a result of a kernel update when I wasn't paying attention. When I try reinstalling with

> sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

I get the message

> The following packages have unmet dependencies:
nvidia-glx: Depends: nvidia-kernel-1.0.9629

When I try to install said package I get:

> Package nvidia-kernel-1.0.9629 is a virtual package provided by: <blank>
You should explicitly select one to install.

This is a bit beyond me. Anyone?

TIA

---

### Post by renzokuken on 2007-01-19
do you know which repo you are trying to get the nvidia packages from? is it a ubuntu official one or a third party one?

---

### Post by bodhi.zazen on 2007-01-19
Best way to run nvidia is with the envy script.

Works like a charm.

You need to install the linux-generic-kernel package :p

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

		From CLI:```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

	Configure: GUI = nvidia-settings

---

### Post by chucklechops on 2007-01-19
> **renzokuken said:**
> do you know which repo you are trying to get the nvidia packages from? is it a ubuntu official one or a third party one?

I just took out the beryl repo and a couple of other suspects and everything worked like a charm, back in business, Cheers guys!:D

---

### Post by renzokuken on 2007-01-19
congratulations, happy ubuntuing

> Package nvidia-kernel-1.0.9629 is a virtual package provided by: <blank>
You should explicitly select one to install.

suggestes that there were two conflicting packages present

---

