---
title: "update kills graphics driver"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by NeillHog on 2007-08-05
I installed Kubuntu and the graphics would not work properly because I have an older NVIDIA graphics card. I had to download an extra driver and install that .

Now - a week later - suddenly there is a new option in my boot menu. Another Ubuntu but with a one higher version number. I selected this and there was no screen content as before. A few days ago I updated everything (adept_updater). Does thais mean that after each update I will have a new option in the boot menu and that I need to reinstall the new graphics driver manually every time?

Sorry if this isn't a very well worded question but I am very new to Linux and Kubuntu.

Thanks!

---

### Post by fimbulvetr on 2007-08-05
You shouldn't have to reinstall drivers on every update.

Go to Applications->Accessories->Terminal and run:

```
dpkg -l | grep kernel
```
```
dpkg-l | grep nvidia
```
```
dmesg
```
```
uname -a
```

And paste the output in a reply.

Note that those are four separate and distinct commands, run each one in succession.

---

### Post by tseliot on 2007-08-05
> **NeillHog said:**
> I installed Kubuntu and the graphics would not work properly because I have an older NVIDIA graphics card. I had to download an extra driver and install that .
If you didn't install the driver from Ubuntu's repositories you will have to reinstall the driver every time the kernel is upgraded.

---

### Post by NeillHog on 2007-08-05
Some more information.

The start menu offers Ubuntu Kernel 2.6.20.15 (that is my original and works) and also the new Ubuntu Kernel 2.6.20.16 (this leaves me with a black screen.

To install the correct driver I had to download it and then do
# cd yourdirectory
# sh NVIDIA-Linux-x86-1.0-9639-pkg1.run

So I guess that means. Yes! If I update the system then I will have to reinstall the driver. This is bad news as the driver installation seems a little buggy and didn't work first time last time meaning a complete new install.

Maybe I need a new graphics card!

Thanks 
Neill


The following is the asked for information for the working 2.6.20.15. Do you also need it for the non working 2.6.20.16?

neill@NeillsPC:~$ dpkg -l | grep kernel
ii  libdrm2                                    2.3.0-1                                Userspace interface to kernel DRM services -
ii  linux-generic                              2.6.20.16.28.1                         Complete Generic Linux kernel
ii  linux-headers-2.6.20-15                    2.6.20-15.27                           Header files related to Linux kernel version
ii  linux-headers-2.6.20-15-generic            2.6.20-15.27                           Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.20-16                    2.6.20-16.29                           Header files related to Linux kernel version
ii  linux-headers-2.6.20-16-generic            2.6.20-16.29                           Linux kernel headers for version 2.6.20 on x
ii  linux-headers-generic                      2.6.20.16.28.1                         Generic Linux kernel headers
ii  linux-image-2.6.20-15-generic              2.6.20-15.27                           Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.20-16-generic              2.6.20-16.29                           Linux kernel image for version 2.6.20 on x86
ii  linux-image-generic                        2.6.20.16.28.1                         Generic Linux kernel image
ii  linux-restricted-modules-generic           2.6.20.16.28.1                         Restricted Linux modules for generic kernels
ii  module-init-tools                          3.3-pre3-1ubuntu7                      tools for managing Linux kernel modules
ii  nvidia-kernel-common                       20051028+1ubuntu7                      NVIDIA binary kernel module common files
ii  udev                                       108-0ubuntu4                           rule-based device node and kernel event mana

neill@NeillsPC:~$ dpkg-l | grep nvidia
bash: dpkg-l: command not found

neill@NeillsPC:~$ uname -a
Linux NeillsPC 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

---

### Post by NeillHog on 2007-08-06
Thinking about this, I assume that an update of packages using the adept updater then starts a recompile (or whatever the technical word is) of the whole Linux system. If this is the case then how should the system know that I have added new NVIDIA drivers manually.

If I change the drivers in my newest version will this have any effects on the older (working version)? I assume not but would like confirmation from an expert.

Thanks!

Neill

---

### Post by Aurdal on 2007-08-06
The configuration files and the kernel are separate enteties.
So should you change any configuration setting (like which graphics driver to use) it will affect both boot options.

---

### Post by alienexplorers on 2007-08-06
Use the Envy script at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
to install your video drivers.  Since using this script I have not had any problems after kernel updates.

---

### Post by NeillHog on 2007-08-06
Thanks for all the help.

I used the method 1 at
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
and now the newer version starts as well. Seems like Alberto Milone really knows his stuff.

Sorry Aurdal - I don't understand.
I don't think that it is a configuration file that is telling the system which driver to use, rather that the driver gets compiled into the kernel and therefore has to be re-added every time - but what do I know - three wekks ago I had never heard of Ubuntu :-)

neill

---

### Post by overdrank on 2007-08-06
> **NeillHog said:**
> Thanks for all the help.

I used the method 1 at
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
and now the newer version starts as well. Seems like Alberto Milone really knows his stuff.
neill

tseliot
If you didn't install the driver from Ubuntu's repositories you will have to reinstall the driver every time the kernel is upgraded.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I would say so. ;)

---

### Post by NeillHog on 2007-08-06
My understanding from reading the various information at [http://www.albertomilone.com](http://www.albertomilone.com) is that no matter what I do I am going to have to go through the NVIDIA update process every time I update my system. Envy is maybe an easier way but it will still have to be done after every update.

Or maybe I am missing something important.

Thanks!

---

