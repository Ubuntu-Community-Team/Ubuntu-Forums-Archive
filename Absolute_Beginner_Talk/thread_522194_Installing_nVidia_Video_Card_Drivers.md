---
title: "Installing nVidia Video Card Drivers"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Stoneysilence on 2007-08-10
Ok, I am a complete newb to Linux. I tried Ubuntu and Fedora Core 6 about 8 months ago. Wasn't impressed and didn't mess around with it much. But during the Summer term in college I decided to take a Linux class. We are using Fedora Core 4 though. Long story short that got me interested in trying Ubuntu 7.04 (64bit) again.

So I installed it and got it co-existing with Vista Business 32-bit alright. But it seems that Ubuntu doesn't recognize my video card which is a EVGA 8500GT(Desktop won't run at greater then 1025x768 and in Linux's "Device Manager" there is a PCI device that is unknown). So I went to nVidia's site and found drivers and it had a installer so I downloaded the installer. But it won't run in X-Windows. So here is my problem, how do I get to a Terminal only screen? I tried rebooting into Safe Mode in GRUB (not sure exact name) which loaded Terminal. But when I went to run the file the program complained about being in mode 1 and not mode 3 or something and said to type telinit 3 something like that. Soon as I typed that then X-Windows loaded and took me to Gnome Desktop.

What do I do? I hate running my desktop at 1024x768 (which is all Ubuntu will let me do right now).  I also tried CTRL-ATL-F2 but it said x-server was still running.

Thanks,
StoneySilence

---

### Post by mikewhatever on 2007-08-10
If you absolutely must install the driver manually, use this guide
[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)
otherwise, use envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Hospadar on 2007-08-10
Hey there, couple things.  If you can't get the drivers working right away and just want to get full resolution, do a ```
sudo dpkg-reconfigure xserver-xorg
``` and when you get to the resolution page, select all the resolution options you want with 'space' and restart you xserver with ctrl-alt-backspace from within gnome, or ```
sudo /etc/init.d/gdm restart
```If you are installing manually from the downloaded driver, you will need to stop your xserver with ```
sudo /etc/init.d/gdm stop
``` (you start it the same way, but replace stop with start) once it's stopped you can install the drivers fine.  make sure you have build-essential installed before attempting the driver install.

All that said, I would use envy to install the drivers and only resort to manual installation if envy fails.
```
sudo apt-get install envy
sudo envy -t
```then remove/clean driver installs, then install the new driver.  If the drivers that envy installs don't work, use envy to remove drivers and clean installation, then install manually the drivers from nvidia.

---

### Post by Ek0nomik on 2007-08-10
> **Stoneysilence said:**
> Ok, I am a complete newb to Linux. I tried Ubuntu and Fedora Core 6 about 8 months ago. Wasn't impressed and didn't mess around with it much. But during the Summer term in college I decided to take a Linux class. We are using Fedora Core 4 though. Long story short that got me interested in trying Ubuntu 7.04 (64bit) again.

So I installed it and got it co-existing with Vista Business 32-bit alright. But it seems that Ubuntu doesn't recognize my video card which is a EVGA 8500GT(Desktop won't run at greater then 1025x768 and in Linux's "Device Manager" there is a PCI device that is unknown). So I went to nVidia's site and found drivers and it had a installer so I downloaded the installer. But it won't run in X-Windows. So here is my problem, how do I get to a Terminal only screen? I tried rebooting into Safe Mode in GRUB (not sure exact name) which loaded Terminal. But when I went to run the file the program complained about being in mode 1 and not mode 3 or something and said to type telinit 3 something like that. Soon as I typed that then X-Windows loaded and took me to Gnome Desktop.

What do I do? I hate running my desktop at 1024x768 (which is all Ubuntu will let me do right now).  I also tried CTRL-ATL-F2 but it said x-server was still running.

Thanks,
StoneySilence

You should be able to get to a command line only interface by hitting Control+Alt+F1 during the booting process.  Just go crazy hitting it, yout can't screw anything up.  ;)

---

### Post by igknighted on 2007-08-10
> **Ek0nomik said:**
> You should be able to get to a command line only interface by hitting Control+Alt+F1 during the booting process.  Just go crazy hitting it, yout can't screw anything up.  ;)

You can get to the CLI easily, the problem is stopping X.  You need to use the command ```
/etc/init.d/gdm stop
``` in order to stop the xserver, then do the install (you will need the build-essential package, available through apt, in order for the driver installer to build a module for your kernel).  From here on Nvidia's directions should work.

---

### Post by Stoneysilence on 2007-08-10
> **Hospadar said:**
> 
```
sudo apt-get install envy
sudo envy -t
```then remove/clean driver installs, then install the new driver.  If the drivers that envy installs don't work, use envy to remove drivers and clean installation, then install manually the drivers from nvidia.

When I try sudo apt-get install envy it says package not found.

> (you will need the build-essential package, available through apt, in order for the driver installer to build a module for your kernel)

How do I do this?

---

