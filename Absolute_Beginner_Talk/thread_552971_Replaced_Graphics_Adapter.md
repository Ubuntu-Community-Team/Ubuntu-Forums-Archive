---
title: "Replaced Graphics Adapter"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-09-17
Hi,

I've just purchased a new graphics adapter for my PC, and want to instal it tomorrow. I've done this before with XP, so that's no problem. However, I'm unsure of how I approach revising the drivers in Ubuntu.

Would it be simpler to re-install Ubuntu after I've loaded the new drivers (NVIDIA) in XP (I dual boot)? The current Ubuntu instal sniffed ouyt the existing card, so could I assume re-installing might do the same?  If not, where could I find a manpage on installing the drivers from within Ubuntu? I downloaded the Linux drivers from NVIDIA tonight.

I'd appreciate any help or comments. Thanks

---

### Post by hyper_ch on 2007-09-17
Doing anything in windoze will (at least should) not do anything to your linux install.

If you have Feisty or Gutsy, replace the video card and then just run the Restricted Drivers Manager. That should install the current drivers.

---

### Post by Perfect Storm on 2007-09-17
By CLI, you properly can't get into X when switching card;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install nvidia-glx
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

By the way which card did you bought? Reason is if it's a very new brand, you properly need to get the latest driver from nvidia.com

---

### Post by w4ett on 2007-09-17
There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by corowakid on 2007-09-18
> **Artificial Intelligence said:**
> By CLI, you properly can't get into X when switching card;

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install nvidia-glx
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

By the way which card did you bought? Reason is if it's a very new brand, you properly need to get the latest driver from nvidia.com

Its a 3DForce 6200-256. I doubt it would be the most current card of that genre.

---

### Post by corowakid on 2007-09-18
> **w4ett said:**
> There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

Thanks - I'll be doing it tonight. I've read of the preference for FOSS of using generic drivers, so I'll give that a go first.

---

