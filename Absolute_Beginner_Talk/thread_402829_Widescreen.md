---
title: "Widescreen"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by mystically on 2007-04-06
I'm using a laptop on widescreen however with ubuntu it doesn't work. It have 2 black strips at the sides of my screen. I tried editing xorg.conf with 1280*800 being the only number there but it doesn't work, It's still a squar. Please help me how to get widescreen to work,

---

### Post by msaied on 2007-04-06
just enable the universe in the software sources then open a terminal and do apt-get update 
then
apt-get install 915resolution
then reboot

---

### Post by mystically on 2007-04-06
Still didn't work the resolution 1280x800 still didn't display on the screen resolution menu.

---

### Post by msaied on 2007-04-06
whats the laptop make and model?

---

### Post by mystically on 2007-04-06
Toshiba Satellite
A100

My sound card doesn't work too. It works for beep but nothing eles.

Nothing on xorg.conf is edited now it's all default

Im running on Virtual PC 2007 full screen mode.

---

### Post by msaied on 2007-04-06
your laptop ether have an  Nvidia GeForce or ATI MOBILITY RADEON depending on its model
if it was a native installation I would say that installing the drivers will sure fix it but you mentioned installing in a virtual PC  so i am not confident that it will work , even with the drivers (i am not sure about Virtual PC but emulation software in general tend to emulate a standard VGA compatible device to the guest os)

installing Nvidia driver:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")
installing ATI drivers:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29")

---

