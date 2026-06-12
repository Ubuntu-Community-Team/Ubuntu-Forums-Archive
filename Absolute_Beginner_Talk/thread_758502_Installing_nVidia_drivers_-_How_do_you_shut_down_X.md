---
title: "Installing nVidia drivers - How do you shut down X?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Sootah on 2008-04-18
I am attempting to install the latest drivers from nVidia so that I can get my 8800 GTS working first, at the correct Hx (currently monitor is set to 50 with no better alternative) and 2, so I can have dual monitors.

I was all kinds of excited when I did the initial install and saw at least the cloned view. After letting the "latest" (how do you check the version, anyway?) drivers from nVidia install my second screen is now dark and there is no option to enable it.

Trying to shut down the X system has been frustrating because I cannot find consistent instructions on how to do it. Init 1 from the command line works, but I am unable to install the drivers from this mode.

I want to do nothing more than kill the X windows system, install the nVidia drivers, and reinitialize X.

Can anyone help me?

Thanks,

-Sootah

---

### Post by Sootah on 2008-04-18
Driver I am attempting to install - [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by chewearn on 2008-04-18
A good way to install nvidia driver (if you are unhappy with the driver in the ubuntu official repositories) is to use envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Else, to answer your question...


1. Ignore the 50Hz horizontal frequency; it an anomaly due to the way the nvidia driver is hacked.  You should check the actual monitor frequency via the monitor OSD / setup menu.


2. For setting up your display, use:
```
gksu nvidia-settings
```You can also check your driver version there.


3. To shutdown X, ALT+CTRL+F1 to go to text console, login, then run:
```
sudo /etc/init.d/gdm stop
```
To start X:
```
sudo /etc/init.d/gdm start
```

---

### Post by Sootah on 2008-04-18
Found this - [http://www.nvnews.net/vbulletin/showthread.php?t=111871](http://www.nvnews.net/vbulletin/showthread.php?t=111871)

Anybody care to offer some explinaion as to how all of this is supposed to work? Seriously all I want is good performance, my rez/refresh rate to be correct, and dual monitor support.

---

### Post by bumanie on 2008-04-18
I have done this before, but not for a while. I hope my memory is good!
ctrl-alt-F1 to stop xserver then enter username password
> cd ~/Desktop (if that's where you've downloaded the nvidia .run file to)
> sudo /etc/init.d/gdm stop
> sh NVIDIA-Linux-x86-169.12.pkg1.run
> sudo /etc/init.d/gdm start
> reboot
Hope this is correct, as I said it's a while since I've done it.

---

### Post by caravel on 2008-04-18
**AstalaVista** is correct.  My refresh rate shows up as 50Hz as well but my monitor is at 85Hz.

---

### Post by Sootah on 2008-04-18
> **AstalaVista said:**
> 
2. For setting up your display, use:
```
gksu nvidia-settings
```You can also check your driver version there.


Ran that in the terminal, it asked for my password, and then nothing happened. Am I doing something wrong?

Also, what is "gksu"?

---

### Post by caravel on 2008-04-18
Driver not installed?

gksu runs a process with administrative privileges.  It is used for running graphical apps, whereas sudo is used for terminal apps.

---

### Post by chewearn on 2008-04-18
> **Sootah said:**
> Ran that in the terminal, it asked for my password, and then nothing happened. Am I doing something wrong?

Probably, *nvidia-settings *not installed.  Install the nvidia driver first.  *nvidia-settings* comes with the driver.

> Also, what is "gksu"?

Like *caravel* said.

---

### Post by Sootah on 2008-04-18
Using Envy and then the nvidia-settings I was able to get it working. Ubuntu has been impressive in some ways so far, but a huge pain in the *** in others.

Thanks all for your help. (This forum is crazy responsive)

---

### Post by caravel on 2008-04-18
I've used envy in the past but now I use the existing driver that is enabled via the restricted drivers manager.

For newer geforce cards, nvidia-settings is now part of nvidia-glx-new for anybody trying to find or install it in synaptic.

Glad you got it working **Sootah**, you've had it relatively easy.  The ATI driver is much more difficult to set up.

:)

---

