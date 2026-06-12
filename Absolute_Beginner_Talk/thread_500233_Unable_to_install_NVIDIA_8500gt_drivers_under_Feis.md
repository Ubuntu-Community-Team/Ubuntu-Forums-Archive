---
title: "Unable to install NVIDIA 8500gt drivers under Feisty"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by l33t5241494E on 2007-07-13
So I decided to crack down and finally do a dualboot with ubuntu and windows xp professional on my new computer. Everything installs great and I get feisty fawn up and running. I decided I wanted 3D acceleration for my nvidia 8500GT. I downloaded the latest drivers off nvidia's website. I then got libc6 and libcdev through synaptic. Afterwards I proceeded to install the drivers under root in commandline. Greeted by a bios-like screen I followed the instructions and rebooted. X wouldn't start, so I changed the xorg.conf back to it's original and it booted up. I then put this into terminal:

sudo gedit /etc/default/linux-restricted-modules-common

and added "nv" under disabled. Replaced unworking xorg.conf and rebooted. Still X will not start. I've reformatted and tried to install these drivers about 16 times. Any helpful advice would be much appreciated. Thanks in advance.

---

### Post by Cappy on 2007-07-13
Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

As the nvidia script runs, allow it to configure X (xorg.conf).

Once you are in X you can configure (dual monitors, resolution, etc) with ```
gksudo nvidia-settings
```[/QUOTE]

---

### Post by l33t5241494E on 2007-07-14
That did it. Thanks man. Hopefully it will continue to work after a restart or too. That way I don't have to reformat a 17th time!

---

