---
title: "It won't let me install nvidia drivers"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-11-26
If I go to add or remove and try to mark nvidia-glx-new for installation I get
```

NVidia binary X.Org driver ('new' driver) cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```
But I've installed these drivers before and had them working fine. I just did a fresh install and want to get compiz-fusion running (Which I have had working on this same PC) but this driver won't install.
Any Help?

---

### Post by GSF1200S on 2007-11-26
> **microsoft92sucks said:**
> If I go to add or remove and try to mark nvidia-glx-new for installation I get
```

NVidia binary X.Org driver ('new' driver) cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
```
But I've installed these drivers before and had them working fine. I just did a fresh install and want to get compiz-fusion running (Which I have had working on this same PC) but this driver won't install.
Any Help?

What nvidia card you have? Can you post the results of:
```
lspci
```
in a terminal please...

Have you tried the restricted drivers manager? We should be able to get you sorted..

---

### Post by microsoft92sucks on 2007-11-26
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```
Yes, restricted drivers manager tells me to install nvidia-glx-new.

---

### Post by GSF1200S on 2007-11-26
Hmm weird... 

You said you did a fresh install, and your banner says you run 7.04- so im guessing you upgraded to 7.10 right? I think Feisty still used the Nvidia 9755 driver, where Gutsy uses the newest driver. If you are in fact moving from Fawn to Gibbon, I would suggest downloading the nvidia binary 9755 from the website and install it from the command line.. I had to do it to get video accel working on fawn, so I can walk you through that.

Its funny though.. your card seems to fall into the new driver- theres no reason it shouldnt work.

So, is this a 7.04 to 7.10 upgrade, or what?

---

### Post by microsoft92sucks on 2007-11-26
I've had the driver running on 7.10 before, I had 7.10 ever since it's been beta (I forgot all about that banner I'll change it soon.) And this is the first time I've had any trouble with the drivers. accept the very first time I tried to install them, And all I did was a reinstall of Ubuntu and they've worked perfect for every reinstall til now. (I reinstall OS's a oddly large amount of times. Not sure why. :wink:) So  a simple reinstall should fix this, Unless you known some other way to fix this?

It won't let me install the older drivers eathere it says the same thing.

---

### Post by alienexplorers on 2007-11-26
I am running a FX-5200 card and I had to try loading restricted drivers multiple times and then it took.  Was kind of odd, but now things work great.

---

### Post by microsoft92sucks on 2007-11-26
I'll try a reboot later, It may work I'll play around and if I can't get it I'll just reinsstall thanks for all the help.

---

### Post by GSF1200S on 2007-11-26
This might be a stupid question but have you updated apt? I know that the drivers were updated a time or two since gutsy went BETA, so perhaps its looking for a driver that isnt there? A simple apt-get update should fix that.. thats the only thing I can think of really...

---

### Post by microsoft92sucks on 2007-11-26
No that didn't work. But still thanks for all the help I think I'll do a fresh install tomorrow.

---

### Post by alienexplorers on 2007-11-26
Have you tried using the ENVY script to load your drivers.  In past versions I relied on this to load my drivers.

---

### Post by aktiwers on 2007-11-26
You did not by mistake download 64bit drivers and own a 32bit computer? Just guessing here...

---

### Post by microsoft92sucks on 2007-11-26
No I'm trying to install it through add or remove, and it keeps saying that but I never got that before. So I'll just reinstall because I'm having other problems with this install. (I can't get gOS desktop installed.)

---

### Post by aktiwers on 2007-11-26
Did you try install them manually?


Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1
Log in
 type:
```
cd Desktop
```And then
```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```when done.. type:
```
sudo reboot
```

---

### Post by LowSky on 2007-11-26
try using synaptic instead of add/remove.

BTW gOS isn't all its cracked up to be..I got a liveCD of it and all I can say is it need a little more polishing. I know its built on ubuntu but E17 isn't for me

---

### Post by microsoft92sucks on 2007-11-26
I got the drivers working by doing a fresh install. I don't know what happened in my last install but it works fine now.

I kinda like gOS I had it installed on a 2nd partion for a while but I want gnome, e17 (gOS), and KDE I like having several Gui's.
I'm getting ready to attempt to get gOS desktop installed and working now hopefully a fresh install will fix it.

Thanks for all the help :)

---

