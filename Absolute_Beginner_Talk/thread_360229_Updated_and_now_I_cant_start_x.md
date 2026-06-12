---
title: "Updated and now I cant start x"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Sou Portugues on 2007-02-12
So I clicked the update icon, and when I did the restart, my x wont come up.  It tells me that the screens are unconfigureable.  I was running twinview with nvidia driver I got from envy.

Not sure where to start now, but suggestions would help.  I'm running the install disk as a live cd, so I don't know what kind of acces to my sytem would be from terminal.

Is there some sort of backup program or way to take a "system creenshot" so to speak in the future, as to avoid this sort of quandry?

---

### Post by rabid emu on 2007-02-12
You can downgrade or remove certain packages if you know what package screwed your system up.

Also, I'd try out "dpkg-reconfigure xserver-xorg" in a terminal.  It will reset your xorg config and you can reselect what driver to use, as well as resolution and stuff.

---

### Post by Sou Portugues on 2007-02-12
> **rabid emu said:**
> You can downgrade or remove certain packages if you know what package screwed your system up.

Also, I'd try out "dpkg-reconfigure xserver-xorg" in a terminal.  It will reset your xorg config and you can reselect what driver to use, as well as resolution and stuff.

That would be great, does the code line there give me some sort of dating (I could just undo the ones I did today)?

---

### Post by azazel00 on 2007-02-12
I run into this problem everytime I update the kernel.

The thing is, that aparently the Nvidia driver needs to be recompiled/readdded/re-whatever, after the kernel upgrade.

Just do
```
sudo sh ./NVIDIA-file.run
```

In case you need to download the driver, (since you got it from a repo), here's a command:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

Then just run it. Remeber to tell it NOT to configure xorg when it asks, or you might loose some settings.

Regards,
az

---

### Post by Sou Portugues on 2007-02-12
Thanks, I'll give that a try.

Is there a way to prevent that in the future (I'd like to continue to update the kernael when available)?

---

### Post by azazel00 on 2007-02-12
Well, so far, my guess is "no". If you notice, the NVIDIA installer has to compile the module for the particular kernel. Being that the kernel does not include the custom nvidia driver with it, everytime you update the kernel you are pretty much starting fresh.

I just do it everytime I upgrade. Always keep the drive file at hand. It's a bit tedious, but I'd rather have the latest kernel than avoid reinstalling the driver.

---

### Post by C-A on 2007-02-13
If you have envy installed. Use envy to uninstall your nvidia driver. Then, use envy to install the nvidia driver.

---

### Post by tonyr1988 on 2007-02-13
I had the same problem after updating (I used envy originally as well). If you haven't gotten it fixed yet, do this after you get the error:

Ctrl + Alt + F1

Login with username / password

> sudo envy

Uninstall nVidia driver

> sudo envy

Install nVidia driver

NOTE: As of now, you'll have to do this anytime you do a kernel update. Luckily, it doesn't take long and if you consistently use envy each time you shouldn't have any other difficulties - I haven't.

---

### Post by coolen on 2007-02-13
I got this this morning. The reason has already been posted, but thew problem will persist until Nvidia releases open source drivers (or until an open source equivalent becomes available and usable).
I use the beta driver, so until the repos are updated, I'm sticking with the old kernel. Worked fine for me for ages.
Oh, and if you run into this problem again and don't want to have to resort to a Live CD, you can hop back to a terminal and edit your xorg.conf file. Tell it to use the nv driver instead of nvidia. It's a bit lacking, but hey, it works, and you can then work on your system directly.

---

### Post by PartisanEntity on 2007-02-13
> **coolen said:**
> I got this this morning. The reason has already been posted, but thew problem will persist until Nvidia releases open source drivers (or until an open source equivalent becomes available and usable).
I use the beta driver, so until the repos are updated, I'm sticking with the old kernel. Worked fine for me for ages.
Oh, and if you run into this problem again and don't want to have to resort to a Live CD, you can hop back to a terminal and edit your xorg.conf file. Tell it to use the nv driver instead of nvidia. It's a bit lacking, but hey, it works, and you can then work on your system directly.

I'm still not sure I understand. Who wrote the 8776 nvidia driver which is in the ubuntu repo? And how does it differ from the 9746 driver on the nvidia website? What has to happen so that perhaps the 9746 nvidia driver gets taken up into the ubuntu repo?

Thanks!

---

### Post by Perfect Storm on 2007-02-13
8776 driver is Nvidia so it the 9xxx driver. The new driver will be in the next ubuntu release (april month).

---

### Post by frodon on 2007-02-13
> **Sou Portugues said:**
> Is there a way to prevent that in the future (I'd like to continue to update the kernael when available)?If you use the nvidia drivers from the repo you will never have this problem.
Each drivers you compile (nvidia, wirelees and so on) need to be installed again and again each time you change kernel, it's why i never advice to use the latest nvidia drivers for beginners.

Hope your problem is now solved :)

---

### Post by PartisanEntity on 2007-02-13
> **Artificial Intelligence said:**
> 8776 driver is Nvidia so it the 9xxx driver. The new driver will be in the next ubuntu release (april month).

Thank you for the information, will that apply in any way to dapper?

---

### Post by Perfect Storm on 2007-02-13
Every release do only get security updated, so if you want the new driver on Dapper you need to do it manually.

---

### Post by NeoDesign on 2007-02-13
I'm sorry, but I cannot seem to install the NVidia 9746 driver. When it tries to build the kernel modules, it comes up with an error saying it cannot load the nvidia.ko module. What can be the problem? Are there additional packages needed for this build to work??

I am now using envy, but I don't have direct3d rendering -- and it is a great pain!

Thanks all, in advance

---

### Post by Perfect Storm on 2007-02-13
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
sudo /etc/init.d/gdm start

```

---

### Post by Sou Portugues on 2007-02-14
For those from the beggining...
My system went totally kaput, had to wipe and re-install.  Now starting over, but would like to not do the shotgun effect of downloading everything and installing everything until something works.

> **frodon said:**
> If you use the nvidia drivers from the repo you will never have this problem.
Each drivers you compile (nvidia, wirelees and so on) need to be installed again and again each time you change kernel, it's why i never advice to use the latest nvidia drivers for beginners.

Hope your problem is now solved :)

Either I don't know what I'm looking for, or I havent enabled the correct repo's to see the nvidia driver.  Isthere a way to tell if I have the right one?

---

