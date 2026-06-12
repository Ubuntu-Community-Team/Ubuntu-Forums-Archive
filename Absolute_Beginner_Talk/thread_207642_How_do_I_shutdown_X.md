---
title: "How do I shutdown X"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Dazaablack on 2006-07-02
Hi,

I am trying to install a nVidia Graphics Driver for my GF6600GT card. 
I installed bitutils but it says I need to shut down X so I can run it.

I have no idea how to do this with Ubuntu.

do I kill a process or something?

Please help.

---

### Post by simonn on 2006-07-02
Log out of your gnome session.

Switch to a terminal using ctrl + alt + F{1-6}.

```

$ sudo /etc/init.d/gdm restart

```

---

### Post by Dazaablack on 2006-07-02
Thanks Simon,

I managed to shut down x using the /etc/init.d/gdm stop

This Nvidia Driver is a nusance and is telling me that its:
Unable to find the kernel source tree for the currently running kernel. Please make sure toy have installed the kernel source files for your kernel.

I am running damper 6.06.

Does this mean I am missing some kernel source files.
I tried 
sudo apt-get install kernel-source

and its downloading a 31mb file.

---

### Post by simonn on 2006-07-02
[QUOTE=Dazaablack]
Does this mean I am missing some kernel source files.
[/quote]

Yep.

> 
I tried 
sudo apt-get install kernel-source

and its downloading a 31mb file.

You need the linux-headers-[kernel version] package. However...

I would suggest that you use the packages in the repository, this will probably save some headaches.

Off the top of my head...

nvidia-glx
nvidia-kernel-common
linux-restricted-modules-common
linux-restricted-modules-[kernel version]

---

### Post by tseliot on 2006-07-02
You can try one of my guides:
Guide for Dapper
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

Guide for Breezy
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by steve.horsley on 2006-07-02
Is there any reason why you are not using the driver that Ubuntu provides? It's much easier than doing a custom compile. If it's just that you didn't know that Ubuntu repositories provide a driver, try the following:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by Drakkor on 2006-07-02
Question: I can't use the 2.6.15-23-686 kernal with nvidia-glx ?? Thanks

---

### Post by simonn on 2006-07-03
Question: You should be able to ?? That's ok.

---

