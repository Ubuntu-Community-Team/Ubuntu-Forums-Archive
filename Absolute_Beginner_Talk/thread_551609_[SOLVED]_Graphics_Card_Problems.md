---
title: "[SOLVED] Graphics Card Problems"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-09-15
(EE)Failed to load module "nvidia"(module does not exist, 0)
(EE)No drivers available.

any help?? i know its something like sudo apt-get nivida-legacy or something but its been a while since ive mest with linux any help?? Nividia 7300

---

### Post by slimdog360 on 2007-09-15
what?

---

### Post by w4ett on 2007-09-15
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

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

### Post by cerealtx on 2007-09-15
everything worked great!!! thank u very much for all of your help

---

