---
title: "Nvidia driver causes X server failure"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by OldDog11 on 2007-04-02
I have just installed the nvidia-glx package and now my system has crashed.

Failed to start the X server.

I have tried reverting to the original graphics driver but the file is not recognised.

I have Feisty AMD 64 bit installed  and a nvidia 7300GS graphics card, any ideas?

---

### Post by Bachstelze on 2007-04-02
You also need the restricted-modules for your current kernel :

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

### Post by Dual Cortex on 2007-04-02
OK, press CTRL+ALT+F1, then issue the command
sudo dpkg-reconfigure xserver-xorg. When selecting the driver to use, choose vesa.

Then when you're not in panic (since a broken x *usually* brings panic to users... because of the scary black screen needed to be used), open up a terminal and type 
sudo apt-get install build-essentials
Then use the following instructions (from a fellow forum member) to use Envy to install nvidia's drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I prefer this over the nvidia-glx option since (I'm not completely sure since it was a while ago that I installed my nvidia drivers) installing the package installs the old 8776 drivers.

---

### Post by Bachstelze on 2007-04-02
It's *build-essential* (no "s"). Also, I don't recommend using Envy.

---

### Post by land0 on 2007-04-02
after the system boots and the x-server dies do the following.

press Ctrl+Alt+F2

At the login prompt enter your username then password when asked for it. 

Once you are logged in type the following **sudo dpkg-reconfigure xserver-xorg** 

You can then set your video card and monitor back to the default by answering all the questions you are presented with. 

Once you have reconfigured the xserver it will dump you at the command prompt again.

Type the following **sudo /etc/init.d/gdm restart** enter your password if prompted. 

That should get you back into the gui.

---

### Post by OldDog11 on 2007-04-02
Many thanks for your help.

I don't have time to try any of it now but I will do as soon as I can.

---

