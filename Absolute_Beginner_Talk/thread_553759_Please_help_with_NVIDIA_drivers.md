---
title: "Please help with NVIDIA drivers"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Knightsky on 2007-09-18
[B]***SOLVED!***
(Thank you everyone!)[/B]


I´m very excited to be using Ubuntu finally...though I´m running into problems that I haven´t for the life of me been able to fix. The specific flavor I'm using is Ubuntu Studio 7.04 which apparently has a lowlatency kernel. My machine is brand new, an Intel Core Duo 6750 with the additional specs:

2gb of Corsair Ballistix ram
EVGA 680i motherboard
EVGA NVIDIA GeForce 8800 GTS Superclocked video card
Seagate 320gb hard drive with 16mb buffer

I've tried installing NVIDIA drivers using the following methods:
Easy Ubuntu
Automatix
NVIDIA's own NVIDIA-Linux-x86-100.14.11-pkg1.run file
and a series of steps which I learned about through here: [http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126) (Method 1 online, and Method 2 online)

One thing that struck me as odd is that nvidia-config has not been able to write to the config file. This was in the command line, having shut down the Gnome GUI using CTRL+ALT+BKSPCE

...the forum just recommended I read Tayyeb's guide, and I will...but with all the different ways I've tried to get this going, I'm not sure not posting what I've done is the best option...so I'll post and read.

---

### Post by philinux on 2007-09-18
Have a look here.
[http://ubuntuforums.org/archive/index.php/t-468353.html](http://ubuntuforums.org/archive/index.php/t-468353.html)

---

### Post by Knightsky on 2007-09-18
Thank you for the link, that was another method of installation that I hadn't tried.

Unfortunately, it also failed. *sigh* Here are the two error messages I get:

-----error #1-----
API Mismatch: this NVIDIA driver component has a version 100.14.11 but the NVIDIA kernel module's version does not match.
(EE) NVIDIA(0) Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in the system and that the NVIDIA device files have been created properly.

-----error #2-----
Fatal: Error running install command for NVIDIA
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
***Aborting***
(EE) Screen(s) found, but none have a usable configuration.


so apparently I need to do something with the kernel module, that much is clear...but I have no idea what to do and how to go about doing it. I must again ask for your help, everyone.

---

### Post by r4ik on 2007-09-18
Seems to me you haven't tried Envy yet,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by Knightsky on 2007-09-18
> **r4ik said:**
> Seems to me you haven't tried Envy yet,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

Thank you very much, I'll look this over right away!

---

### Post by w4ett on 2007-09-18
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

### Post by r4ik on 2007-09-18
Would be nice if you let us know what happened never mind if it was bedtime just drop a post later.

---

### Post by Knightsky on 2007-09-18
Thank you both of you! Envy did the job and admirably! Of course, I guess I have to try a reboot and see what happens, but this is the best sign I've seen this week!

---

### Post by r4ik on 2007-09-18
> **Knightsky said:**
> Thank you both of you! Envy did the job and admirably! Of course, I guess I have to try a reboot and see what happens, but this is the best sign I've seen this week!

Reboot you will be save.

---

### Post by Knightsky on 2007-09-19
> **r4ik said:**
> Reboot you will be save.


Yup, everything's working great. Thank you very much!

---

