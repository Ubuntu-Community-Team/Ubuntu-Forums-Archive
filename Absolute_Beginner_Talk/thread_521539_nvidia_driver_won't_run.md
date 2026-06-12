---
title: "nvidia driver won't run"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by natialos on 2007-08-09
I have Kubuntu Feisty, and I installed the nvidia driver for my GeForce FX 5200 or 5400 (forgot which), and whenever I change my xorg.conf to have "nvidia" and then reboot, the reboot gets stuck right near the very end, after loading timidity. I don't think timidity is at fault, however, I think it's just the last thing to load.
Whenever I switch the driver back to "nv", it loads just fine.
Any ideas?

---

### Post by Ek0nomik on 2007-08-09
> **natialos said:**
> I have Kubuntu Feisty, and I installed the nvidia driver for my GeForce FX 5200 or 5400 (forgot which), and whenever I change my xorg.conf to have "nvidia" and then reboot, the reboot gets stuck right near the very end, after loading timidity. I don't think timidity is at fault, however, I think it's just the last thing to load.
Whenever I switch the driver back to "nv", it loads just fine.
Any ideas?

Are you sure you installed the correct driver?  Which one did you install, and how did you go about installing it?  From the repository or from the nVidia website?

---

### Post by jake16424 on 2007-08-09
imcompatible? possibly currupt,, idk, i had a problem after i installed all updates for ubuntu it wouldnt boot from the hard drive anymore, so i had to format again,, but ima  newb at this os, so idk. O_O

---

### Post by natialos on 2007-08-09
> **Ek0nomik said:**
> Are you sure you installed the correct driver?  Which one did you install, and how did you go about installing it?  From the repository or from the nVidia website?
I've tried both. I also tried running envy. All of them install great, but when it comes time to reboot... it stops.

---

### Post by Vague on 2007-08-09
In Feisty you should be able to install that driver from the Restricted Devices Manager and not have to mess with your xorg.conf at all.

---

### Post by benx009 on 2007-08-09
> **Vague said:**
> In Feisty you should be able to install that driver from the Restricted Devices Manager and not have to mess with your xorg.conf at all.

yes, this is the best way for installing the nvidia drivers

---

### Post by natialos on 2007-08-09
> **benx009 said:**
> yes, this is the best way for installing the nvidia drivers
I can't seem to find this Restricted Devices Manager. I have kde. Is it included in that, or do I have to go out and install it? If it's included, what menu path do I use to get there?

---

### Post by Ek0nomik on 2007-08-09
> **natialos said:**
> I can't seem to find this Restricted Devices Manager. I have kde. Is it included in that, or do I have to go out and install it? If it's included, what menu path do I use to get there?

I am quite positive it doesn't come with KDE.  You will have to install it seperately.  I believe it is in the repository though.

**Edit**:  'sudo apt-get install restricted-manager' should do the trick.

---

### Post by Vague on 2007-08-09
> **natialos said:**
> I can't seem to find this Restricted Devices Manager. I have kde. Is it included in that, or do I have to go out and install it? If it's included, what menu path do I use to get there?

I'm pretty sure Kubuntu Feisty has it.  For me it's under Applications>System>Restricted Devices Manager, but that probably won't be terribly useful for you, since I'm not running Kubuntu.  Someone who is can probably be of more help.  If you don't think you have it, just open up a terminal and enter ```
sudo apt-get install restricted-manager
```

Edit:  Or. . . maybe it doesn't come with it.  I could have sworn it popped right up with ATI and wireless drivers when I installed Kubuntu on a laptop, though.

---

### Post by natialos on 2007-08-09
> **Ek0nomik said:**
> I am quite positive it doesn't come with KDE.  You will have to install it seperately.  I believe it is in the repository though.

**Edit**:  'sudo apt-get install restricted-manager' should do the trick.
 
Okay.... so now I installed it, but I don't see it in my menu. I checked under settings, system, and utilities, which seem the only logical places for it to be, and it's not under any of them. :confused:

---

### Post by Ek0nomik on 2007-08-09
> **natialos said:**
> Okay.... so now I installed it, but I don't see it in my menu. I checked under settings, system, and utilities, which seem the only logical places for it to be, and it's not under any of them. :confused:

It may not have added a menu entry, which I do find weird.

You can always run it from the terminal:

```
restricted-manager &
```

should do the trick.

---

### Post by natialos on 2007-08-09
> **Ek0nomik said:**
> It may not have added a menu entry, which I do find weird.

You can always run it from the terminal:

```
restricted-manager &
```

should do the trick.

okay, that worked, but didn't do much. It showed me that my Nvidia card is enabled but not in use. What am I supposed to do from there?

My terminal gave me the message:

> modinfo: could not find module nvidia_legacy


Thank you for all of your help, by the way!

---

### Post by Ek0nomik on 2007-08-09
> **natialos said:**
> okay, that worked, but didn't do much. It showed me that my Nvidia card is enabled but not in use. What am I supposed to do from there?

My terminal gave me the message:




Thank you for all of your help, by the way!

There should be a box which you can check to download and install the proper drivers for your card.

---

### Post by natialos on 2007-08-09
> **Ek0nomik said:**
> There should be a box which you can check to download and install the proper drivers for your card.
The only box I see to check is the "enabled" box. I checked that and then it said I needed to restart my computer. So I did, and got stuck again just like I always do.

---

### Post by Ek0nomik on 2007-08-09
> **natialos said:**
> The only box I see to check is the "enabled" box. I checked that and then it said I needed to restart my computer. So I did, and got stuck again just like I always do.

Well, back to the building blocks I suppose.

You said you weren't 100% sure of your card model.  Could you run this and post the relevant output:

```
lspci
```

---

### Post by natialos on 2007-08-09
> **Ek0nomik said:**
> Well, back to the building blocks I suppose.

You said you weren't 100% sure of your card model.  Could you run this and post the relevant output:

```
lspci
```

I have the GeForce FX 5200

---

### Post by MenZa on 2007-08-09
It really isn't as difficult as all this; I'm not entirely sure whether the FX5200 uses nvidia-glx or nvidia-glx-legacy, but I guess we could try both.

First try running the following commands:

```

sudo apt-get install nvidia-glx linux-restricted-modules-common linux-restricted-modules-generic

```

Ensure that the driver in your xorg.conf is specified as 'nvidia'. Then try starting X (sudo /etc/init.d/gdm restart [or kdm if you're on KDE]). If this doesn't work, try doing:

```
sudo modprobe -r nvidia && sudo lrm-manager && sudo modprobe nvidia
```

If this doesn't work, pay attention to the error message, and paste it here.

---

### Post by natialos on 2007-08-09
> **MenZa said:**
> It really isn't as difficult as all this; I'm not entirely sure whether the FX5200 uses nvidia-glx or nvidia-glx-legacy, but I guess we could try both.

First try running the following commands:

```

sudo apt-get install nvidia-glx linux-restricted-modules-common linux-restricted-modules-generic

```

Ensure that the driver in your xorg.conf is specified as 'nvidia'. Then try starting X (sudo /etc/init.d/gdm restart [or kdm if you're on KDE]). If this doesn't work, try doing:

```
sudo modprobe -r nvidia && sudo lrm-manager && sudo modprobe nvidia
```

If this doesn't work, pay attention to the error message, and paste it here.

The first one made me stop again while rebooting, although it did stop earlier in the booting process, right before it usually 'loads the necessary files' or something like that.
I got this error message after the second one:

FATAL: Error inserting nvidia (/lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia.ko): No such device

---

### Post by natialos on 2007-08-09
Okay, so I googled that error and ran the following command that was supposed to fix it, and now I've got a strange other error:

```
[login protected]:~$ sudo updatedb
Password:
[login protected]:~$ locate nvidia.ko
/home/-----/NVIDIA-Linux-x86-1.0-8776-pkg1/usr/src/nv/nvidia.ko
/home/-----/NVIDIA-Linux-x86-1.0-8776-pkg1/usr/src/nv/.nvidia.ko.cmd
/lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko
[login protected]:~$ sudo modprobe -r nvidia && sudo lrm-manager && sudo modprobe nvidia
**not loading nvidia_new module; not used in /etc/X11/xorg.conf**

```

---

### Post by natialos on 2007-08-10
And when I change my xorg.conf to have nvidia, I get this:

```
FATAL: Error running install command for nvidia
```

---

