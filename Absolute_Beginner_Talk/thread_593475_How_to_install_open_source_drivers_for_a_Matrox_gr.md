---
title: "How to install open source drivers for a Matrox graphics card"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-10-27
Hello Everybody,

As I can't get Compiz to work with my Intel integrated graphics, I bought a Matrox Millienium G550 graphics card. I disabled the Intel in the BIOS and downloaded the open source driver from Matrox's website. It's a tar.gz file. I managed to unzip it and now have a folder on my desktop but I don't know how to proceed from here. 

In the bad old days when I used to run Windoze, I would double click the exe file to install the driver, but I don't know what to do in Linux. The folder contains 3 folders called xserver, docs and samples and a file called install.sh. What do I do next? 

Hoping that somebody can help, as I just spent 80GBP and am looking at an 800x600 screen!

Thanks,

Charlie

---

### Post by tehet on 2007-10-27
Hi,
After a quick search I found **xserver-xorg-video-mga**
> Description: X.Org X server -- MGA display driver
 This package provides the driver for the Matrox MGA family of chipsets,
 including Matrox Millennium and Mystique cards.
so I think you can just install it from the repositories.

---

### Post by Charlie Chick on 2007-10-27
> **tehet said:**
> Hi,
After a quick search I found **xserver-xorg-video-mga**

so I think you can just install it from the repositories.

Synaptic says that it's already installed, but Screens & Graphics says that it's not as Open Source Driver is greyed out. Also, it won't allow me to reset screen resolution, or rather it will, but then says that I have to log off and back on again, after which I'm back to square 1.:(

Thanks,

Charlie

---

### Post by tehet on 2007-10-27
> **Charlie Chick said:**
> Synaptic says that it's already installed,
Ok, so building the tar.gz probably won't help you any further. Perhaps you need to edit your /etc/X11/xorg.conf file to enable it (but I don't know what the name of the driver is).
nVidia example:
```
Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        **Driver          "nvidia"**
        BusID           "PCI:1:0:0"
```
Anothr thing you could try is
```
sudo dpkg-reconfigure xserver-xorg
```
and when you get to the bit where you can select the driver, look for something called MGA (that would be my best guess but I don't know).

---

### Post by Charlie Chick on 2007-10-27
Update: I logged into the Terminal as root and dragged the install.sh script into it. That then asked me for the location where the files should go and I found that in the readme file on the Matrox website. 

Unfortunately, when it ran, it came up with an error message saying "The X server drivers included in this installation package do not support the current version of your X server."

So it looks as if I've just wasted 80GBP - unless anybody knows different?

Charlie

---

### Post by Meserias on 2008-02-05
Same problem here ! How can I enable 3D acceleration for a MATROX G450 card ?
What I need to configure ? .... simple steps.:confused:

---

