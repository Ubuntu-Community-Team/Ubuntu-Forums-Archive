---
title: "Compiling Realtime PPC Kernel"
date: 2007-05-24
forum: Apple PPC Users
---

### Post by johng4 on 2007-05-24
[I][B][COLOR="Red"]This is not my work so much as it is a combination of several tutorials I've found from "How To Forge" and the Ubuntu Forums.

I've tried and failed on doing this several times, and each time I've learned something that the previous attempt had left out.  In my last attempt I got it right, and I'll share the experience.[/COLOR][/B][/I]

[CENTER]** This is the easiest method.  You can get more indepth, but if all you want is a real time version of you current working kernel (with a slight upgrade to the 2.6.21 kernel) follow this guide. **[/CENTER]

**_Step 1: Preperation_**
First things first.. lets get the packages we need for compiling a new kernel.
```

$ sudo apt-get install kernel-package libncurses5-dev wget bzip2

```

There's plenty of ways to work in a root enviroment, I perfer:
```

$ sudo bash

```

You can do whatever you perfer.

**_Step 2: Get your kernel**_
Go to [www.kernel.org](www.kernel.org) and grab the current stable kernel.  At the time of this writing its 2.6.21.2  To get the right kernel choose the "F" option for the full kernel source.

Download it to you home directory.

Then, change into the source directory...
```

#cd /usr/src

```

Copy the downloaded tar file of the kernel...
```

#mv /home/(yourname)/linux-2.6.21.2.tar.bz2 /usr/src

```

...and untar it...
```

#tar -xjf linux-2.5.21.2.tar.bz2

```

**_Step 3: Setting up the Kernel**_
Now that we have an unpacked kernel, lets create the neccessary links to it:
```

#ln -sfn linux-2.6.21.2 linux 

```

Now change into the directory we just symlinked:
```

#cd linux
[CODE]

Now, we begin the fun stuff.  At this point you have the option of installing kernel patches if so wish to.  If you want to know how to do that, please refer to [this tutorial]("http://www.howtoforge.com/kernel_compilation_ubuntu?").   This tutorial is aimed at setting up a realtime kernel, so I won't distract you with the other fun things you can get involved in with Kernel Customization.

At this point we have all the needed tools to get started.  Now its time to get the configuration file for our current kernel to load into the source of this kernel:

First, get the name of your current kernel:
[CODE]
#uname -r

```

Then, copy that into the following line:
```

#cp /boot/.config-(your kernel name) ./.config-realtime

```

Now we have all we need in place to configure the kernel to work like our kernel, only with the additions we need to add, in this case real time preemption.

**_Step 4: Configuring your kernel**_
Now we break into the kernel's configuration and enable what we want.  To get the configuration menu type:

```

#make menuconfig

```

Scroll down to the bottom of the menu and choose "Load an Alternate Configuration File."  It will ask for a file name, type in ".config-realtime."

Now go to "Kernel Options" and select "Timer Frequency" and set it to "1000 Hz."
While under "Kernel Options" also change "Preemption Model" to "Preemptible Kernel (Low-Latency Desktop)."

Once you've done this you've done all you need to do to enable realtime preemption.  You can further customize your kernel, but unless you know what you're doing, it is ill advised.

At this point you can hit Esc a few times and you'll be prompted to save the Configuration.  Say "yes" and you'll be back at the CLI.

**_Step 5: Creating the Kernel Packages**_
Now we'll create a .deb package for the kernel to allow for easy installation and uninstallation (in case we do not like the results).

```

#make-kpkg clean
#make-kpkg --initrd --append-to-version=-realtime kernel_image kernel_headers

```

[CENTER]
**!!!WARNING!!!**
This will begint he compiling process.  This means that your computer will be very busy for a fairly lengthy period of time.  As such, if you're doing this on a machine other people expect to use, or is run on a battery.. or there's a chance of power outage.. hold off on this step until you have a few hours to spare.
[/CENTER]

**_Step 6: Installing the Kernel_**
Okay, now you've compiled your new kernel, packaged it, and hopefully not starred at your screen for 2 or more hours.  Now its time to install it.

Change to the source directory...
```

#cd /usr/src

```

In this directory, you'll see the "linux-image-2.6.21.1-realtime_2.6.21.1-realtime.10.00.Custom.powerpc.deb" and "linux-headers-2.6.21.1-realtime_2.6.21.1-realtime.10.00.Custom.powerpc.deb"  Using dpkg we'll install both of these .debs.

```

#dpkg -i linux-image-2.6.21.1-realtime_2.6.21.2-realtime.10.00.Custom.powerpc.deb
#dpkg -i linux-headers-2.6.21.1-realtime_2.6.21.2-realtime.10.00.Custom.powerpc.deb

```

**_Step 7: Update Yaboot**_
We have the kernel configured, compiled and installed.  Now we just need to set it up to boot.  This part can cause some severe problems, so be careful in what you edit.

Open up the yaboot.conf file...
```

#nano /etc/yaboot.conf

```

Add the following stanza into the file...

```

image=/boot/vmlinux-2.6.21.2-realtime
        label=Realtime
        read-only
        initrd=/boot/initrd.img-2.6.21.2-realtime
        append="quiet splash"

```

Ctrl-O to save, then Ctrl-X to exit.

After that we just update yaboot...
```

#ybin -v

```

Now.. close your terminal, and restart your computer.  When the prompt for the Stage 2 section of yaboot comes up, type "Realtime" and it will boot your new realtime PPC kernel.

Enjoy.

I can't garuntee that they'll work, but here's the kernel image and headers that I compiled.  Let me know if they work.

[Realtime PPC 2.6.21.1 Kernel Image and Headers]("http://linux.tuneforge.net/ppc-linux/realtime-ppc-kernel.tar")

---

### Post by stmiller on 2007-05-24
Thanks this is great. I strongly suggest running a 

make g5_defconfig

or 

make pmac32_defconfig

instead of just copying the past ubuntu kernel config. The ubuntu ppc config is not very optimized for your computer (it is made to work on ALL macs) and doing a specific config for your system is perhaps better. 

This also enables all recent powerpc fixes done in a new kernel which you might miss otherwise. (Esp for G5 machines and thermal stuff).

---

### Post by johng4 on 2007-05-24
The reason I pull the current one, is when I did the make def_(model) version, I had to re-enable all my networking stuff.  When I first compiled it I didn't, and as a result did not have any drivers for my networking devices.

When I pulled the current working config file, it worked fine with no extra configuration.

The next step for me is creating a tutorial for configuring the kernel to load an optimized kernel for ppc.  I'm fairly to kernel configuration, so I'm going to take my time there.  Either way, the goal of the next kernel I build to be a machine specific kernel with only the options selected that involve my machine.  

When I get done with that I'll post a how-to on that as well, since most Macs will have an easier time of customizing the kernels due to predictable hardware.

---

### Post by franzpv on 2007-06-14
It just worked...as simple as that. Now, I would like to know how to uninstall it because I want to try to build a specific Kernel for my Powerbook G4 12". I noticed during the "make" process that a lot of drivers were compiled and wich hadrdware I don't even have them.

NOTE: I had to re-install the bcm43xx-fwcutter in order to get the Airport Extreme running.

---

### Post by stmiller on 2007-06-14
> **franzpv said:**
> It just worked...as simple as that. Now, I would like to know how to uninstall it because I want to try to build a specific Kernel for my Powerbook G4 12". I noticed during the "make" process that a lot of drivers were compiled and wich hadrdware I don't even have them.

NOTE: I had to re-install the bcm43xx-fwcutter in order to get the Airport Extreme running.

You can go and remove what you don't need in the 'make menuconfig' step. I usually remove RAID, and various unneeded things. Or simply doing a 

make pmac32_defconfig

before the make menuconfig will enable just the bare minimum you need for a G4 machine. Might still have to enable the broadcom after that.

---

### Post by franzpv on 2007-06-15
I tried with the make pcmac32_defconfig but didn't work. Then, I installed the libraries needed to run "xconfig" and went checking everything on the kernel configuration. I left only what I needed....I think....then continued with the process described above. Now, I'm writing on my new and optimized kernel. :)

Note: Left keyboard support out :P and now it doesn't automount Usb Pendrives. Soon I'll be posting the .config I used if someone wants to try it.

---

### Post by franzpv on 2007-06-25
When I tried with the "make pmac32_defconfig", the driver for the Airport Extreme was left out.  I checked the .config file and the option dind't even appear on it. I had to use the old .config that comes with precompiled kernel of Ubuntu and remove everything I didn' t need.

---

