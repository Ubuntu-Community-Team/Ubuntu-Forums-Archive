---
title: "MacBook Pro 6.2 Nvidia card not shown."
date: 2013-03-09
forum: Apple Hardware Users
---

### Post by sw3ex on 2013-03-09
Hy,

I just installed ubuntu as a second OS on my MBP and everything works (more or less) fine excepts for the graphics. As a reminder it has two graphic cards: the integrated intel one and a Nvidia 330M GT.
I already solved the graphics unkown problem by installing the mesa-utils. So now it shows I have an intel Gallium. I would like to use my Nvidia but the drivers don't show up under system sources-> additional drivers.
Any idea how I can fix this? And is there any way to switch between the two cards (manually if I have to).

---

### Post by Mr. Shannon on 2013-03-09
Are you saying you have an optimus graphics setup.  If that is the case then you could try [http://bumblebee-project.org/](http://bumblebee-project.org/).  It allows you to launch a program and have it's graphics handled by the NVIDIA card.  You can install with the following commands.
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install linux-headers-generic bumblebee bumblebee-nvidia

```
[B]
EDIT[/B]: That card does not say it supports optimus, so I don't really know how your integrated+dedicated graphics are setup.  The above may work, or it may leave you without a graphical environment (probably fixable).

---

### Post by sw3ex on 2013-03-09
The fact is that on the community documentation pages of the MacBook Pro 6.2/Precise (there is no support page for the 6.2/quantal) it says this:
> **Video & Effects (Compiz)**

 [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=restricted.png[/IMG]  You  should use the restricted video driver: The open source driver nouveau  seems to currently causes random system freezes. Also with the  powermizer functionality of the Nvidia driver you can get the laptop  pretty cool at about 50 degrees Celsius instead of 65-70 degrees.  Battery life is also better at about 4 hours currently (instead of  2:30). 
Install from: System -> Administration -> Hardware Drivers. Select the NVidia graphics driver that says recommended and Activate.  Reboot to apply the change. 
Edit your /etc/X11/xorg.conf to permanently operate the Nvidia graphics adapter in the lowest possible setting: 

gksu nvidia-xconfig #if you haven't created a xorg.conf yet gksu gedit /etc/X11/xorg.confAdd the following lines to the Device section of the nvidia device: 


Option  "Coolbits" "1" Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"

But on my system the Nvidia card is not listed. I tried once to install bumblebee but after rebooting I got a warning saying that X was running in low graphic mode.

side note:
Ubuntu is really my second OS wich I use for some programming and running Xilinx. My machine is always connected to a power source when booted in Ubuntu so battery life is not that important but I would like to have the power of my dedicated graphics. So I would already be happy if I could just change my configuration to use that card, switching would be more a nice addition.

---

### Post by Mr. Shannon on 2013-03-09
In non Mac computers there is sometimes a setting in the BIOS to use the dedicated graphics card all the time.  However, I am not sure how this would work on a mac since it does not have a BIOS.  Also, after reading though this thread ([https://discussions.apple.com/thread/2770866?start=0&tstart=0](https://discussions.apple.com/thread/2770866?start=0&tstart=0)) at Apple it seems that the switchable graphics don't work in windows installed with bootcamp either (except windows seems to be stuck with the dedicated graphics).  You may just be out of luck.  However, considering that the community documentation says it should work there is probably something else going on here.  Hopefully someone with experience running Linux on a Mac will come by and help you.

---

### Post by sw3ex on 2013-03-09
Thanks, I've done some more reading also, but surprisingly I found that most of the users have the inverse problem and are indeed stuck with the dedicated graphics and that they need some special boot options to boot using the integrated. So I guess I need to find the boot options to boot using my dedicated card.

---

