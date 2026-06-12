---
title: "Can't enable visual effects"
date: 2009-02-18
forum: Beginner Team
---

### Post by ktat on 2009-02-18
Hi, firstly, I'm new here, if I'm posting in the wrong place sorry for that- please redirect me...

My problem is this, after trying to enable visual effects immediately after installation and failing I installed compiz-check and ran it, the summary I got was this:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Unknown device 0641 (rev a1)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
```

It seems it was unable to locate a suitable driver for my card. I am using:

    * AMD Athlon 64x2, 5200+ 2.7Ghz Dual core AM2 CPU
    * Gigabyte GA-M56S-S3 motherboard
    * 2 Gb DDR2 RAM
    * 512Mb Geforce 9400 GT PCI-EXPRESS Video Card
    * OS Ubuntu 8.04


Some help with this would be appreciated :)

---

### Post by ronelc on 2009-02-18
you can try to download the new driver here:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

it worked for me. it should work for you.

regards

---

### Post by ktat on 2009-02-18
> **ronelc said:**
> you can try to download the new driver here:

[http://www.nvidia.com/object/linux_display_ia32_180.29.html](http://www.nvidia.com/object/linux_display_ia32_180.29.html)

it worked for me. it should work for you.

regards

Thanks for the quick reply, I downloaded and installed the file, then ran it from the terminal, unfortunately this was the response:


```
:~$ sh NVIDIA-Linux-x86-180.29-pkg1.run

ERROR: this .run file is intended for the
Linux-x86 platform, but you appear to be
running on Linux-x86_64.  Aborting installation.
```

Any other ideas?

---

### Post by overlord.gaurav on 2009-02-18
Download the driver from [here]("http://www.nvidia.com/object/linux_display_amd64_180.29.html").

---

### Post by ktat on 2009-02-18
Thanks overlord.gaurav, again I've run into a small problem.
After starting up from the terminal, the program told me I had to exit the X server.  I don't know how to do that, so I had a look at the README on the [[COLOR="Blue"]nvidia[/COLOR]]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.29/README/appendix-i.html") site and it said:

> Unlike many desktop operating systems, it is relatively easy to cause irreparable damage to your Linux system. If you are unfamiliar with the use of Linux, we strongly recommend that you seek a tutorial through your distributor before proceeding.

Is there such a tutorial, I really don't want my system to crash and burn!

---

### Post by overlord.gaurav on 2009-02-19
**1. Just in case, your driver doesn't work take a backup of your xorg.conf:**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
[B]
2.Install the nvidia-settings package:[/B]
```
sudo apt-get install nvidia-settings
```

**3.Place your driver file in your home folder. Close all open windows. Press CTRL + ALT + F1. Login to your admin account. Kill your GDM session:**
```
sudo killall gdm
```
[B]
4. Now install the driver:[/B]
```
sh NVIDIA-Linux-x86_64-180.29-pkg2.run
```
Follow the steps and complete the installation.
[B]
5. Once the installation is complete, reboot your computer:[/B]
```
sudo reboot
```


**SOURCE:** [http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

---

### Post by ktat on 2009-02-23
Thanks, I gave this a try and everything workded fine up to the point of rebooting.  Unfortunately, I still can't enable desktop effects and now the screen resolution is screwed up (all icons and windows etc considerably larger).

> **overlord.gaurav said:**
> **1. Just in case, your driver doesn't work take a backup of your xorg.conf:**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


I tried replacing the xorg.conf with the backup but was told I don't have authority. [B] Please, what are the steps to restoring my system?

[/B]

---

### Post by overlord.gaurav on 2009-02-25
That command was to take the backup of xorg.conf
To restore the backup, do this in a terminal:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by overlord.gaurav on 2009-02-25
There is one more way to installing proprietary nVidia drivers: by installing [Envy]("http://albertomilone.com/nvidia_scripts1.html").

To install Envy, do this:
```
sudo apt-get install envyng-gtk
```

Then run Envy, you'll find it in Applications  > System Tools
OR
Open a terminal and type:
```
 envyng -t 
```

Follow the on-screen steps and install the driver that suits you.
Hope this solves your problem.

---

### Post by ktat on 2009-03-04
No luck with previous suggestion, however, I think I've found my driver at [[COLOR="Blue"]http://www.nvidia.com/object/linux_display_amd64_180.29.html[/COLOR]]("http://www.nvidia.com/object/linux_display_amd64_180.29.html").

This is how I finally got it to work...
> 1. Press Ctl+Alt+F1
2. type user name and password.
3. type $ sudo /etc/init.d/gdm stop It'll say [OK] and the edge of your screen
4. I downlded the Nvidia Dvr To /home/username/Downlds dir on my system.
commands: $cd /home/username/Downlds
$sudo sh ./NV press tab to autocomplete
answer and read all the Questions so say Yes to all and don't forget to chose to allow x.org to be auto configed!!!
5. $sudo reboot. and It worked beautifully.
above quote was sourced from **tulambin** in another thread.

I realise now it's the same driver as pointed out by **overlord.gaurav** earlier, i think it worked this time through because the **nvidia settings package** is problematic and so the driver install works better without it.

---

