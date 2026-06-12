---
title: "Nvidia drivers in feisty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-04-22
How do i install nvidia drivers in feisty fawn?

---

### Post by Vorian on 2007-04-22
system>administration>restricted drivers manager

---

### Post by Istonian on 2007-04-22
thanks

---

### Post by Billium on 2007-04-22
I have an nVidia GeForce 6150 graphics card.
When I go into restricted manager it says Ubuntu may be using driver software that cannot be supported, and is not checked.

What do I replace it with?

I tried to download glx but when I rebooted I got a floating thing from HP that would not go away and said I was using a driver that was not supported.

I reinstalled feisty and now I'm afraid to try anything.

I'm not comfortable with command lines, but I can cut and paste.

Help please, and thanks.

---

### Post by lkjhgfdsa on 2007-04-22
Righty,

I get the same as Billium. I try the System>administration>restricted drivers manager......
and I try to check the box, a dialogue asks me if I would like to enable it, I click enable and nothing happens.

I tried the driver from the NVIDIA site (I am 64 bit).

I have the same problem as this guy [http://ubuntuforums.org/showthread.php?t=418380&highlight=nvidia+driver](http://ubuntuforums.org/showthread.php?t=418380&highlight=nvidia+driver)

I switch to VT1, switch off X and then try running the driver.

It complains that there is no precompiled kernel interface, then it tries to download one and fials to find it, then it tries to compile one in situ and then tells me that I do not have libc files installed.

Would you like the /var/log/NVIDIA-Installer.log?

HELP!
______________________________________________________

E6600 core 2 duo 2.4 GHz
DP965LT
2GB
NVIDIA GeForce 6200 LE
(made for number crunching)

---

### Post by CRIMPS on 2007-04-22
I might have had a related problem with Feisty and NVidia.   

To start...I enabled desktop effects, which edited my xorg.conf file.  When I rebooted I got nothing.  No graphics whatsoever.  When I booted into safe mode I tried to load my backup file which didn't work.  So I booted into XP and opened up my xorg.conf and xorg.conf.bak and I edited them in Notepad.  I rebooted and success.

Maybe someone has a similar problem and this can be of some help to them.  So I don't know if I should just stay away from the desktop effects programs or what.  System info is below.

Z

AMD64, NVidia 6600 GT, 1GB RAM, 200 + 120 GB HDDs, 7.04 + WinXP dualboot

---

### Post by Billium on 2007-04-22
I have an Athlon 64 4000+, but I installed the 32 bit version on the advice of another thread,
Should that make a difference?
Thanks

---

### Post by Repent on 2007-04-22
Can someone tell me why envy doesn't work with Feisty anymore? :(

---

### Post by bitterbug on 2007-04-22
I installed build-essentials and then used the drivers from the nvidia site.

Oddly enough, I don't have an Administration section under System in my menus. And I don't have a Desktop Effects setting either, so I really didn't have the option of going anwhere but the manual method.


Anyone else missing options?

---

### Post by lkjhgfdsa on 2007-04-22
See, now when *I* try to install the build-drivers with

sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r)
 I get:-

E: couldn't find package build -essential

So it is as much use to me as a chocolate hammer

---

### Post by Derspankster on 2007-04-26
> **Repent said:**
> Can someone tell me why envy doesn't work with Feisty anymore? :(
It's not supposed to be needed since the "Restricted Driver" Manager has been added to Feisty. Which is fine but it doesn't seem to work for a lot of us.  I had to reinstall my Nvidia 6200 card and when I did I now have no mouse arrow, just a large fuzzy square. Haven't been able to figure out why or how to fix this. I did an upgrade from Edgy.  I've thought about doing a fresh install but kind of figure I'll still end up right here again.

---

### Post by petri on 2007-05-05
Have you tried to install "nvidia-glx" with Synaptic? After installation edit xorg.conf and change the driver "nv" to "nvidia" and reboot.

---

### Post by tommcd on 2007-05-05
In fiesty there is now nvidia-glx and nvidia-glx-new. There is still the nvidia-glx-legacy also. 
See this from tseliot:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
And this from the wiki:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
nvidia-glx-legacy = 71xx driver
nvidia-glx = 96xx driver
nvidia-glx-new = 97xx driver.
List of cards supported by each driver:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
To enable run "sudo nvidia-xconfig" according to tseliot. However, in synaptic if you search for the driver it says to enable with "sudo nvidia-glx-config enable". I think both will work. If you installed to the wrong driver you will need to completely remove it before you install the right one.
You can also use the driver from nvidia by following "method2" from tseliot's guide.

---

