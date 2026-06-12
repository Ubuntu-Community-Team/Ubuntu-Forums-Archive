---
title: "Nvidia Graphics"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-29
The Restricted device Manager is not automatically detecting and installing the correct driver. How do I do this manually using the command line? The card is an Nvidia 7600 GS

---

### Post by taurus on 2007-04-29
Have you tried using envy?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Wake Rider on 2007-04-29
> **taurus said:**
> Have you tried using envy?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Couldn't install it, couldn't install all dependencies

---

### Post by Midgetmunky13 on 2007-04-29
question! What is envy?

---

### Post by Wake Rider on 2007-04-29
I accidentally mounted the partition containing windows which has Nvidia installed on it. Do you think this could be conflicting and stopping the Restricted Device Manager from detecting the Linux Driver? The Restricted Driver Manager worked perfectly for me before I setup the dual boot.

---

### Post by Wake Rider on 2007-04-29
I uninstalled Nvidia from Windows but it didn't help. The Restricted device Manager is picking up that it does have an Nvidia card, but when I click enable, the computer does something for a few seconds then goes slack. It won't allow me to enable the driver. It is an Nvidia GeForce 7600 GS card. What do I need to type into the terminal to force install a driver?? 

I have tried various phrasing of Nvidia using "sudo apt-get install" but it is still not working. Please, does anybody know the precise commands that will make this work. I've tried the envy but it won't even install that for me. This needs to be done manually with commands. The commands I need are the alternative to using the Restricted Device Manager.

---

### Post by ragadanga63 on 2007-04-29
I've tried this on Dapper and worked well for me.  but havent' upgraded to Feisty yet.  Have you tried using automatix2?

---

### Post by benson444 on 2007-04-29
I have a 7600GT card and this worked for me

sudo apt-get install linux-restricted-modules-`uname -r`
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable

I run the first command as nvidia always seems to want to install the i386 kernel and modules.

---

### Post by Wake Rider on 2007-04-30
I tried automatix2 and got a 'fatal apt-based error' The driver couldn't be installed. How do I fix this, what commands do I need to type? 

sudo apt-get install linux-restricted-modules-`uname -r`
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable

These didn't work for me.

---

### Post by ZeroWing on 2007-04-30
Hehehe....


I've had the same problem.

Install Evy's unstable version, to get Nvidia's dependencies quickly, but DO NOT RUN IT!

Grab Nvidia's newest binary driver from Nvidia.com

Rename the bin file to something catchy (so you don't forget the name of the file.

Shut down GDM(/etc/init.d/gdm stop) . Got to tty 1 (alt+ctrl+F1)

Cd to your desktop.

type in sh Catchyname.bin

The driver installer will complain about missing a kernel module or something. Just click no on it, and (oddly enough) it will install without any issues.

Start GDM again(/etc/init.d/gdm start)

Now, the resolution will be dreadfully small, so reconfigure Xorg.

sudo dpkg-reconfigure xserver-xorg

And make sure you select your driver. Check the resolutions you want after it asks you about you mouse and keyboard, and select medium when it asks you how you want to configure your monitor. The rest should be easy.

Restart X. Ctrl+alt+backspace

Sorry if my little guide sucks, but such is life.

 [EDIT] Evy's got a problem with Feisty, and it wont detect the dependencies on the first try. Just wait. Restart your machine. Restart X. Yep.

---

### Post by koconnor100 on 2007-04-30
> **Midgetmunky13 said:**
> question! What is envy?

Envy is a program designed to automatically install nvidea restricted drivers and configure them.

Unfortunately , the author seems to have forgotten that you're problably in 600x 480 graphics mode when you run it , so you can't see the bottom half of the screen and thus effecticvely can't use it in the first place !

*sigh*

Yes, I'm a bitter Envy user, currently watching while my Ubuntu machine slowly reinstalls because it crashed and burned due to driver issues. Not Envy though ... couldn't run envy. Couldn't see most of envy ... so it didn't do any damage ....

---

### Post by Wake Rider on 2007-04-30
> **ZeroWing said:**
> Hehehe....


I've had the same problem.

Install Evy's unstable version, to get Nvidia's dependencies quickly, but DO NOT RUN IT!

Grab Nvidia's newest binary driver from Nvidia.com

Rename the bin file to something catchy (so you don't forget the name of the file.

Shut down GDM(/etc/init.d/gdm stop) . Got to tty 1 (alt+ctrl+F1)

Cd to your desktop.

type in sh Catchyname.bin

The driver installer will complain about missing a kernel module or something. Just click no on it, and (oddly enough) it will install without any issues.

Start GDM again(/etc/init.d/gdm start)

Now, the resolution will be dreadfully small, so reconfigure Xorg.

sudo dpkg-reconfigure xserver-xorg

And make sure you select your driver. Check the resolutions you want after it asks you about you mouse and keyboard, and select medium when it asks you how you want to configure your monitor. The rest should be easy.

Restart X. Ctrl+alt+backspace

Sorry if my little guide sucks, but such is life.

 [EDIT] Evy's got a problem with Feisty, and it wont detect the dependencies on the first try. Just wait. Restart your machine. Restart X. Yep.

Thank you so much. I followed all of your instructions to the letter, and now when I go into the Restricted Device Manager, it is telling me that the Nvidia Graphics card is in use, which is a giant step forward. 

One more question though. I'm not happy with the highest resolution being 1024 x 768 (I'm on a 19" widescreen LCD). That is as high as the resolution will go. How do I use the terminal to select a higher resolution??

---

### Post by ZeroWing on 2007-04-30
> **Wake Rider said:**
> Thank you so much. I followed all of your instructions to the letter, and now when I go into the Restricted Device Manager, it is telling me that the Nvidia Graphics card is in use, which is a giant step forward. 

One more question though. I'm not happy with the highest resolution being 1024 x 768 (I'm on a 19" widescreen LCD). That is as high as the resolution will go. How do I use the terminal to select a higher resolution??

 Reconfigure Xorg again and check what resolutions you want.

 If you already did that, go to Applications ==> System tools ==> NVIDIA X Server settings. Go to the X Server display configuration. The rest should be pretty easy.

 sudo dpkg-reconfigure xserver-xorg to reconfigure via terminal.

---

