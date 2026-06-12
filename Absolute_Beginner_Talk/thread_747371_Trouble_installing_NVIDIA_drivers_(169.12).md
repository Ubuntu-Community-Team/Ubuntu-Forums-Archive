---
title: "Trouble installing NVIDIA drivers (169.12)"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by oblivioncth on 2008-04-06
I have a NVIDIA GeForce 8800 GTS Graphics Card. I just put it in literally 10 minutes ago. Well I enabled the restricted drivers and restarted. Well everything looked fine until I noticed video tearing. I went to go turn VSYNC on and noticed the driver version. On the website there were newer drivers than the ones ubuntu installed default. So I Downloaded the new drivers to my home/downloads folder and on the website ([http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html))
it said type, "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. So I did in the terminal and it said, "sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run"

Any Ideas?

---

### Post by threegremlins on 2008-04-06
try sudo ./NVIDIA.......pkg1.run

to anyone else looking on this thread for answers, I recommend getting the nvidia drivers from the nvidia website, if the old one doesn't work in hh

---

### Post by Chriis on 2008-04-07
I did it with this procedure.
print it on paper before begining

GET DRIVER (nvidia.com)(put it in your /home folder)

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop
sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION and ACCEPT ALL DEFAULT

sudo /etc/init.d/gdm start

Then start configuration by sudo nvidia-xconfig

and voila!

Chriis

---

### Post by stchman on 2008-04-07
> **oblivioncth said:**
> I have a NVIDIA GeForce 8800 GTS Graphics Card. I just put it in literally 10 minutes ago. Well I enabled the restricted drivers and restarted. Well everything looked fine until I noticed video tearing. I went to go turn VSYNC on and noticed the driver version. On the website there were newer drivers than the ones ubuntu installed default. So I Downloaded the new drivers to my home/downloads folder and on the website ([http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html))
it said type, "sh NVIDIA-Linux-x86-169.12-pkg1.run" to install the driver. So I did in the terminal and it said, "sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run"

Any Ideas?

Use Envy 0.9.10.  When you select manual install you can select the 169.12 drivers.  Worked on my Feisty install.

Make sure you remove any Nvidia driver before installing.  Envy can do that for you.

---

### Post by threegremlins on 2008-04-09
Thanks Chriis, I knew there had to be a way of getting out of X so you could install the nvidia driver. usually I just commented out the line that specified the nvidia driver(device) in xorg.conf and rebooted. I'll remember this and I'll have to check out envy too, I know nothing about it.

---

### Post by Hobo Joe on 2008-04-09
> **threegremlins said:**
> 
to anyone else looking on this thread for answers, I recommend getting the nvidia drivers from the nvidia website, if the old one doesn't work in hh

To you - and also anyone looking here:

You need to use Envy. Not only is it MUCH easier, but it's much more likely to work.

There's a link in my sig if you don't have it already.

---

### Post by threegremlins on 2008-04-10
Checked it out, much better way to figure out my card      this is the second time I've lost my cursor in this editing window, makes it hard to type. I was trying to say I'll use envy the next time I upgrade, Thanks.

---

### Post by thisiam on 2008-04-10
thanks, i just got the NVIDIA 8600GT for my desktop and i figured i will get some trouble.
this will help im sure.

---

