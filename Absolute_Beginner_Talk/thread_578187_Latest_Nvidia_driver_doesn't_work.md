---
title: "Latest Nvidia driver doesn't work"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-10-17
Hi. I tried to download the latest nvidia driver from Nvidia website. I installed it, and it appeared to work fine until I restarted my system and i got an error message that the gui failed to load. 
The error was something like the kernel module of my driver and the installed driver didn't match versions. The kernel module module version showed as the previous driver I had downloaded and installed. The one I tried to install was "NVIDIA-Linux-x86-100.14.19.pkg1.run". When I got the error I reinstalled the old driver and got the gui back. Its strange because the installer said that it would uninstall the old driver before installing the new one...

I have an Nvidia 7600 GeForce Go card and i'm quite sure I didn't install the wrong driver. Can someone help me with this?

---

### Post by shad0w_walker on 2007-10-17
This happens quite a bit with manual driver updates. You might want to consider using Envy to install the drivers, it automates the dirty work and should clean up issues like this nicely.

EDIT: Forgot to include the link:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by FredB on 2007-10-17
Yes. It is the simplest way to do on edgy (6.10) and feisty (7.04) releases.

With Gutsy (7.10), just use restricted manager ;)

---

### Post by takuhii on 2007-10-17
Envy isn't compatible with Gutsy yet...

---

### Post by FredB on 2007-10-17
Is envy useful with gutsy ? When I installed Gutsy beta, restricted manager installed flawlessly nvidia driver and tweak them correctly... Compiz worked out-of-the-box.

No need of Envy, so...

---

