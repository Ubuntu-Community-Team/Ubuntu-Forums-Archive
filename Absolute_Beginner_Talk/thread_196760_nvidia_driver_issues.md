---
title: "nvidia driver issues"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by reldruH on 2006-06-14
I just switched my desktop to Ubuntu a couple of weeks ago and everything's been going great, except for my graphics driver. I have an nvidia TNT2 m64 card and can't seem to get it to work correctly. The only way I know of to test if it's working is to try and use some of the 3d screensavers (on my first linux computer most of my screensavers wouldn't work until I installed the nvidia driver). So I have two questions: 1. Is there a better way to see if I have a working driver? and 2. Why isn't the driver working? I've been using synaptic and have tried installing both the regular and legacy drivers and neither one seems to do any good. Help?

---

### Post by taurus on 2006-06-14
I assume you already install nVidia driver with
```

sudo apt-get install nvidia-glx

```
Then, make sure you use "nvidia" as a "Driver" in the Device section in /etc/X11/xorg.conf instead of "nv."
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by johnc4510 on 2006-06-14
Here is the wiki on Nvidia cards:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
To test frames per second do this:
Application>Accessories>Terminal
Type in:
glxgears -printfps
Run a may averages as you want and then close the gear window
Type exit in the terminal

---

### Post by johnc4510 on 2006-06-14
Note: the nvidia-glx driver that taurus talks about will not work on that card. It requires the nvidia-glx-legacy driver.

---

### Post by Arnaud_B on 2006-06-14
Hi,
For (1) check stuff in: 
$cat /proc/driver/nvidia 
you might want to make sure agp is enabled: $cat /proc/driver/nvidia/agp/status
Also, try 
$dmesg | grep nvidia
$dmesg | grep agp 
to see if there are error while loading your driver
Finally you might want to have a look the log file:
$ pico /var/log/Xorg.0.log
about (2) well there are many options but did you follow exactly that (also using the linux-restricted-modules-*):
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
Also you might want to check your xorg.conf file has the correct settings to use your nvidia driver:
$pico /etc/X11/xorg.conf
you should find something looking like that (this is mine so it should not be exactly like that for you...):
Section "Device"
        Identifier      "NVIDIA Corporation NV41 [Quadro FX 3450/4000 SDI]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"         "1"
        Option          "NoLogo"        "1"
        Option          "RenderAccel"   "0"
EndSection
the important part are Driver "nvidia" and Option "NvAGP"

Hope this help,
Good luck!
A.

---

### Post by Arnaud_B on 2006-06-14
Also if you want to edit the /etc/X11/xorg.conf file you need to be root:
$sudo pico /etc/X11/xorg.conf
Oh and another stuff.. on some laptop nvidia cards NvAGP (and virtual terminals also in my case...) do not work because the Riva module is loaded... if this is your case you might want to get rid of this module... it was the case on my laptop I just recompiled without it and it worked great but you dont have to... I just find it better...
A.

---

### Post by reldruH on 2006-06-14
[QUOTE=Arnaud_B]Hi,
For (1) check stuff in: 
$cat /proc/driver/nvidia 
you might want to make sure agp is enabled: $cat /proc/driver/nvidia/agp/status
A.[/QUOTE]

Your reply was very helpful, but I have a few more questions about it. I checked to see if AGP was enabled and it is _not_ but when I try to edit that file it won't let me. I'm using nano (and sudo) and when I try to save it I get an Input/Output Error. Is there some other way to edit this file that I should know about? My card is an agp card, so I'm thinking that changing this will go a long way towards fixing this problem.

---

### Post by reldruH on 2006-06-14
I have the nvidia legacy driver installed, but to no avail. I checked in the /proc/driver/nvidia/agp/status file and it says agp was disabled. I have an agp card, but don't know how to change this. I tried doing it in nano, but got errors every time I tried to save. Any suggestions?

---

### Post by johnc4510 on 2006-06-14
sudo gedit /etc/X11/xorg.conf
edit and save

---

### Post by Arnaud_B on 2006-06-14
mmm.. an I/O error for that? well are you sure you did the right command? it should be:
$sudo nano /etc/X11/xorg.conf
you make the change... then, Control+O will save and Control + X will exit...
then you need to restart the xserver...: Control+Alt+Backspace
well you can also edit with gedit, kate or any text editor as long as you are root... 
If you still get this I/O error try to reboot ... maybe in safemode but well I have no idea what could create an I/O error when you save a file sorry...
Good luck!
A.

---

### Post by Oblong_Cheese on 2006-06-14
Hi all, I am having an issue with my nVidia drivers too!

After following the guide on the wiki ([here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28driver%29%7C%28nvidia%29)), once I execute *# sudo nvidia-glx-config enable* I am prompted with a message like so:

> 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


According to [this thread](http://ubuntuforums.org/archive/index.php/t-23941.html), it's OK to go ahead and do what the error says, ie generate a new md5sum for the config file. So I do that, and then I'm able to run *# sudo nvidia-glx-config enable*.

Then of course I have to restart X, and when I do, it crashes.

I view the output of the error message and it's this:

> 
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected

Fatal server error:
No screens found


Unusual I thought. I then view the detailed error output which gives me the entire xorg.conf file, and at the very top it says under "DefaultLayout" it has an entry called "Device" which has the value "ATI Technologies, Inc. Rage XL".

Now, I have no idea where that came from. I must stress this is a *clean* install of ubuntu 6.06 amd64; when installing nvidia-glx and linux-restricted-modules-amd64-k8, synaptic also pulled down another file, which I think may be a kernel image... it was named something like "linux-image-2.something-k8" ... which is potentially the cause of my problems.

I should also mention that the amd64 LiveCD and the initial install both detected my graphics card properly as being an nVidia GeForce 6800GT.

Does anyone know what I have done wrong here to make this error occur?

---

### Post by zxee on 2006-06-14
You could try this command in the shell 'dpkg-reconfigure xserver-xorg' and from that configure script see if you can choose nvidia as your video card driver and see if that sets thing right when you save the configuration, or edit the device section with your favorite editor and change the device to match your driver.

---

### Post by Oblong_Cheese on 2006-06-15
I have fixed it -- it was a simple matter of changing 'nv' to 'nvidia' as the driver.

I don't know why the installer script didn't do that itself, but oh well.

Everything's running shweet now.

---

