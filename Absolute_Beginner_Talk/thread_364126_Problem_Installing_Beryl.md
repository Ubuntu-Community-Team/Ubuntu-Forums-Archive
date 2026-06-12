---
title: "Problem Installing Beryl"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-02-17
I'm trying to install Beryl and I'm following [these (link)]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") instructions. It said:```
direct rendering: No
``` so I followed the link below to [here (link)]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html"). I have an nVidia GeForce2 card so I entered```
sudo aptitude install nvidia-glx-legacy

sudo aptitude install nvidia-settings
```but when I entered```
sudo nvidia-glx-config enable
```it says```
Error: unable to load nvidia kernel driver! Be sure to have installed the nvidia driver for your running kernel.
``` What does that mean and what do I do?

---

### Post by Spike-X on 2007-02-17
I used a program called Envy to download and install the nvidia drivers I needed to run beryl. A quick search of the forums should help you out with that.

---

### Post by Waappu on 2007-02-18
Hi

Try re-install / install latest Nvidia driver

download envy and install it
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.6.1-0ubuntu1_all.deb)
press Ctrl+Alt+F1.
Login virtual terminal and type```
envy
```
select install Nvidia driver

Read official howto use envy from here
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

