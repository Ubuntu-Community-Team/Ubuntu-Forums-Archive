---
title: "ENVY script failed to install nVidia 6200, what next?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by psyopper on 2007-05-14
Hello, and help please...

I've been using Ubuntu Feisty for a few weeks now and decided it was time to upgrade my video card from the crappy onboard Intel 800 series chip to something better. I selected a PNY gForce 6200 because it supported my mobo's 4x AGP.

I installed it and of course X crashed because it wasn't configured correctly. So I ran 

```
 sudo dpkg-reconfigure xserver-xorg
``` to get back into X and Gnome. Once I was back in I downloaded Alberto Milone's Envy script from [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html") and installed it with Deb. Once installed I ran it and let it do it's thing.

When I restarted the machine X failed to load again with the following error:

```

API Mismatch. This NVIDIA driver component has version 100.14.03 but the NVIDIA kernel 
modules version does not match. Please make sure that the kernel module and all NVIDIA 
driver components have the same version.

Failed to initialize the NVIDIA kernel module!
Please ensure that there is a supported NVIDIA GPU in this system and the NVIDIA device 
files have been created properly. Please consult the NVIDIA readme for details

Screens found but none have a usable configuration

Fatal screen error! No screens found

```

When it dropped me back to the terminal I was able to re run dpkg-reconfigure xserver-xorg and boot back into the machine by specifying the "nv" drivers.

So, what do I do now? Is there an easy fix, or do I give up on the easy way and compile the nvidia drivers myself...

Thanks!!

---

### Post by psyopper on 2007-05-14
OK, so I re-ran Envy to remove the driver it installed. When I rebooted I reconfigured X... again...

Then I downloaded the nVidia driver from their site, NVIDIA-Linux-x86-1.0-9755-pkg1.run, stopped x and installed it with sudo at the shell. It couldn't find a compatable kernel so it created a...umm...kernel interface or something. When it was done I started X and things worked. Kind of. The splash screen was all grey and staticy but the Gnome loader looked ok, it was just the background. Once it loaded my desktop things were peachy!

When I rebooted I still get the same error about kernel versions and had to sh the package to make it work. It looks like I'll have to sh this stupid package every time I boot. In fact I'm kind of afraid to reboot. I gotta tell you, it LOOKS fantastic and works like a charm if I go through the process every time, even desktop effects works IOQuake is beautiful, and World of Padman is most excellent! It's just a royal PITA to have to do this every time I boot! 

Is there any help out there?

---

### Post by psyopper on 2007-05-14
I bit the bullet and restarted. Here is the specific error:

```

Error:API Mismatch: The NVIDIA kernel module has the version 1.0-7184
but this X module has version 1.0-9755. Please make sure that the kernel
module and all NVIDIA driver components have the same version.
```

So I am thinking that I know I downloaded and installed 9755 so the new driver is mismatching with the NVIDIA kernel module. But WHAT kernel module?!?

Arrgh!!!

I love Ubuntu, but this really should NOT be this painful!!!

---

### Post by Nythain on 2007-05-14
its not... envy sucks, right up there with automatix... all you really needed to do was sudo apt-get install nvidia-glx-new from a terminal, after making sure all your repos were available by typing gksudo gedit /etc/apt/sources.list and deleting the # before any lines starting with deb and having http:// whatever, saving, and typing sudo apt-get update... its a real simple process that all automatix and envy do is SCREW UP... sorry but those two apps are bad mojo

---

### Post by psyopper on 2007-05-14
Bad mojo... yes I agree.

Do you have any suggestions as to how I get out of this mess?

---

### Post by psyopper on 2007-05-14
RESOLVED!

God bless Google... The resolution is to edit /etc/default/linux-restricted-modules-common to exclude, in my case, "nv"

[https://bugs.launchpad.net/ubuntu/+bug/107646]("https://bugs.launchpad.net/ubuntu/+bug/107646")

It's covered in Lauchpad for Feisty.

FOr those who stumble upon this in the future:

```

sudo gedit /etc/default/linux-restricted-modules-common
```

I changed DISABLED_MODULES='  ' by adding nv so that it read:

DISABLED_MODULES="nv" 

and restarted the machine. It booted right up after that!   Woot!

---

### Post by Nythain on 2007-05-14
well... if your sources.list file is set up with all the repo's available then i would give this a try
sudo aptitude --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
that will make sure all your packages are removed, then i would try
sudo rm /etc/init.d/nvidia-*
not sure if that will be much help, next i would just simply
sudo aptitude install nvidia-glx-new
hopefully that goes well
then
gksudo gedit /etc/X11/xorg.conf
change nv to nvidia if its not already
save
then reboot and hope all goes well... im really not to GREAT at fixing broken driver installs
if that fails then you can attempt to manually install the driver package you downloaded from nvidia again if you still have it... here's some pretty easy directions
sudo aptitude install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo aptitude --purge remove nvidia-glx-new nvidia-glx nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo ln -s /bin/bash /bin/sh
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run     (where XXXX is the version number you downloaded)
sudo ln -s /bin/dash /bin/sh
modprobe nvidia

usually, when manually installing correctly with the package, it will kill any previous attampts at installing the drivers, and install them correctly, just make sure you have the build-essential, linux-headers-`uname -r`, and the xserver-xorg-dev packages installed or the installer wont be able to correctly compile the drivers 

(side note, im not sure if the symlink bash/dash hack is required as of feisty fawn, i havent had to manually install nvidia drivers since edgy)

---

### Post by hobie on 2007-06-01
Envy didn't work for my 6200 card either, nor did the latest driver (9755) from the NVIDIA site.  
I DID get it to work by using the NVIDIA driver 9746 (look in the archive section on the NVIDIA site) and the NVIDIA install script.  Got the complaint that it had to compile something, but it worked nontheless.  Beryl installed smoothly, except for the missing title bars. Fixed that and all is well.

---

### Post by Beatbreaker on 2007-07-12
> **Nythain said:**
> well... if your sources.list file is set up with all the repo's available then i would give this a try
sudo aptitude --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
that will make sure all your packages are removed, then i would try
sudo rm /etc/init.d/nvidia-*
not sure if that will be much help, next i would just simply
sudo aptitude install nvidia-glx-new
hopefully that goes well
then
gksudo gedit /etc/X11/xorg.conf
change nv to nvidia if its not already
save
then reboot and hope all goes well... im really not to GREAT at fixing broken driver installs
if that fails then you can attempt to manually install the driver package you downloaded from nvidia again if you still have it... here's some pretty easy directions
sudo aptitude install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo aptitude --purge remove nvidia-glx-new nvidia-glx nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo ln -s /bin/bash /bin/sh
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run     (where XXXX is the version number you downloaded)
sudo ln -s /bin/dash /bin/sh
modprobe nvidia

usually, when manually installing correctly with the package, it will kill any previous attampts at installing the drivers, and install them correctly, just make sure you have the build-essential, linux-headers-`uname -r`, and the xserver-xorg-dev packages installed or the installer wont be able to correctly compile the drivers 

(side note, im not sure if the symlink bash/dash hack is required as of feisty fawn, i havent had to manually install nvidia drivers since edgy)

i tried your first solution and that didn't work for me - i'm back to "nv" again in the xorg.conf. 

i also tried the second guide in your post and i get this in my /var/log/Xorg.0.log

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

i'm getting problems with thie Kernel module - is there another way around for it? ENVY definately dosen't work with my system

---

### Post by dannyboy79 on 2007-07-12
you guys are not following the guides properly (maybe you are but it's also possible that you used the restricted module manager and it doesn't properly flush out old drivers) and your having conflicts with the various nvidia drivers. follow these steps if you have any card towards the top of this list ([http://us.download.nvidia.com/XFree8...ppendix-a.html](http://us.download.nvidia.com/XFree8...ppendix-a.html)), then use the nvidia-glx-new (which is the 9755 driver within in the repos), any card in the middle section on this list use nvidia-glx, and then at the bottom use nvidia-glx-legacy. These are all in the repo's. NO need for Envy and or restricted module manager as it didn't pick the correct one for me, then I had the API mismatch problem.

Follow the steps in post number 78 here ([http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)) for your specific card and driver.

---

