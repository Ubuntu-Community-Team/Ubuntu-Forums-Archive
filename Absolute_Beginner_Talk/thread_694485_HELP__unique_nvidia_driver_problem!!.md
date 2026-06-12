---
title: "HELP : unique nvidia driver problem!!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by darthshak on 2008-02-12
Hi

     I recently reinstalled gutsy 64-bit. I ran into a lot of trouble while installing the nvidia drivers though. I have a Thinkpad T61, which has a nvidia quadro nvs 140m on it. When I installed the drivers through the nvidia site, the drivers wouldnt work on reboot. Ubuntu would start up in low graphics mode.

Then i tried out the envy installer script. That installed the drivers without a hitch, but that gave a weird problem : Ubuntu would start up in 1440x900, I would see the wallpaper for like 2 seconds in that resolution, then, the screen goes blank and I'm thrown into this ugly 640x480 resolution. I tried reinstalling several times but to no avail.

I also tried out sudo dpkg-reconfigure xserver-xorg, only to find that ubuntu gave the same low-graphics mode warning on install. 

On reinstalling the drivers again from the nvidia site, I checked the xorg.conf system thoroughly and found no issues with it. 

What am I missing here?

---

### Post by rune0077 on 2008-02-12
When you install the driver with Envy, it will also add the "Nvidia settings" utility to your Applications > System Tools (in the menu). Have you tried setting your resolution from there and then hit "Save to xorg". That ought to make the change permanent.

---

### Post by oedha on 2008-02-12
have you change the resolution manually ?
sudo gedit /etc/X11/xorg.conf
under monitor section
but....back up this xorg.conf before it
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back

---

### Post by drtre on 2008-02-12
i think its better to install the driver via synaptic. it'll install the appropriate driver for you. but before make sure you've checked the repositories.

---

### Post by jan quark on 2008-02-12
drtre is right I would also suggest to try first the restricted driver manager to install drivers before starting to experiment with 3rd party applications

---

### Post by rune0077 on 2008-02-12
No, you shouldn't use the Synaptic driver unless it's a last resort. Synaptic installs a five month old driver with a number of known bugs that has since been fixed. Rule number one when it comes to driver use: always use the latest version. 

Envy will always fetch you the latest drivers, and make sure it fits your card and your architecture, and it will configure your xorg.conf far better than Gnome's Restricted Driver Manager. As a bonus, it'll install Nvidia Settings (since it uses Nvidias own installer), which Synaptic won't.

---

