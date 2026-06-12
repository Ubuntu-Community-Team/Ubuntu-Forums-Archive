---
title: "Updating Nvidia driver."
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by Ric95 on 2006-05-06
I found the better drivers in synaptic and installed them, but I think its still using the default nv . How do I pick what driver to use?

---

### Post by bluevoodoo1 on 2006-05-06
cat /etc/X11/xorg.conf
will show you your xorg.conf. Look for the area that looks like this...


Section "Device"
        Identifier      "NVIDIA FX 5500"
        Driver          "nvidia"
        BusID           "PCI:2:9:0"

if it says "nvidia" you have the new driver.

If it doesn't....

from a terminal....

sudo dpkg-reconfigure xserver-xorg

when it asks if it should be done automatically, choose no. Then at the driver page, select "nvidia" instead of "nv" Then go through the rest, hitting enter each time should be OK. Then restart GDM. Ctrl+Alt+F1 and then you might have to login, then...

sudo /etc/init.d/gdm restart (might be a good idea to write that down on paper)

OR

You can also edit your xorg.conf to add the nvidia driver.

let's make a backup first
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo gedit /etc/X11/xorg.conf
will let you edit it. Again look for something like this...
Driver          "nvidia"

This link might be helpful as well
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by Qrk on 2006-05-06
Have you done this?

```
sudo nvidia-glx-config enable
```

If that doesn't work, try

```
sudo dpkg-reconfigure xserver-xorg
```

and change "nv" to "nvidia," though I think nv is still compatable.

---

### Post by Ric95 on 2006-05-06
when I tried 'sudo dpkg-reconfigure xserver-xorg' it asked for bus info for the vid card I'm using ( I had ATI integrated, so I put nvidia in a slot and I'm using that). So instead I used sudo gedit and edited xorg.conf changing 'nv' to nvidia'. Now I broke it. :(    Heh, good thing I set this up dual boot :) 
Before I try 'sudo dpkg-reconfigure xserver-xorg' again, how can I find out that bus info?( from Windoze XP )
*edit* 
I think I found it; PCI x0

---

### Post by Ric95 on 2006-05-06
Fixed ! thanks to you guys. 
I tried configuring xserver a few times. I ended up using is auto detect and just changing that driver item.  It also turns out I needed the legacy driver. 
It still isn't perfect, but now I can finally run Blender 64 bit :)

---

