---
title: "Edgy Eft and old Nvidia issues"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by mountainman101 on 2007-04-14
I have Edgy installed and am trying to get a geforce 2 mx400 card to work.  Right now, xwindows will not start at all.  I have running the server version.  I had to manually install x using apt-get.  I tried to install the lagacy drivers but it says that libglu1-mesa isnt installed, but when I apt-get libglu1-mesa, it says that I already have the latest version.  This is becoming a pain in the ****.

---

### Post by Patrick K on 2007-04-14
Try this. Type "sudo nano etc/X11/xorg.conf" this will open the nano text editor. Locate the lines "Section "Device"". See if "driver" says "nv". If not change it to "nv" (lower case). Save the file and exit nano. Try "startx". Hopefully, the gui will start for you. If not, try rebooting. If "nv" is already there, I don't have other ideas. 

If the GUI starts, I suggest running the Envy script to install the video drivers. It will download the correct drivers and install them for you.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jem7v on 2007-04-14
Actually, I have that same card, and Envy probably Won't install the right driver for you, which I learned from experience.

However, it Will install all the dependencies necessary for the NVidia installer to work properly, which means it's still a useful tool!  Here's how I'd do it.

[Hopefully] get a working X:
1. Make sure you have this package installed (since if you started from a server install it might not be): xserver-xorg-video-nv is the open-source NVidia driver.  (Get it with apt-get or aptitude.)
2. Once you're booted up, get to a command line (i.e., Ctrl+Alt+F1) and log in.  Then...
```
sudo nano /etc/X11/xorg.conf
```
Scroll down until you find the Section labeled Device.  Make sure Driver says "nv" and if it doesn't, change it so it does.  Exit and save (Ctrl+X, y, enter, enter).  (Re)start your X server, such as by doing this (assuming you have GDM installed):
```
sudo /etc/init.d/gdm restart
```
(What did you install to get your X server going?  Did you install one of the ubuntu-desktop packages, or did you just try to install an X server?)

To get the GOODER working driver:
1. Go to the NVidia site for *nix drivers and download the 9631 driver, just in case.  [http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)  Save it somewhere handy, such as your home directory.
2. Download and set up Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3. Run Envy.  Tell it to set up the NVidia driver that is NOT the legacy driver (i.e., not the 7xxx series).  If it gives you the option of the 9631 driver, go for it and see if it works!
4. Chances are that it'll download and install a bunch of dependencies and then it'll end up failing as it actually tries to install the driver.  That's okay if that happens, because we already have the script from step 1!
5. Do this stuff.  First, write down/print out these instructions, then log out and go to a virtual terminal (Ctrl+Alt+F1).  Log in, then...
```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```
Follow the instructions, keep pressing Okay until it's finished.
```
sudo nano /etc/X11/xorg.conf
```
Scroll down until you find the Section labeled Device.  Make sure Driver says "nvidia" and if it doesn't, change it so it does.  Exit and save (Ctrl+X, y, enter, enter).
```
sudo /etc/init.d/gdm restart
```
...should restart your X server with everything intact.  If something doesn't work

---

### Post by mountainman101 on 2007-04-14
ok, I did the apt-get install gdm, and xwindows tries to start now.  I keep getting errors thats killing it though.  The first is no device /dev/wacom and the second is unable to find "Fixed" font.  As to installing xwindows I mentioned earlier, I did apt-get install xserver-xorg, that was it.

---

### Post by jem7v on 2007-04-14
Are you trying to build a workable desktop environment?  If so, I'd recommend installing ubuntu-desktop, kubuntu-desktop, or xubuntu-desktop depending on your taste in desktop environments.  Those three packages Should install all the packages you need for things to get working.

---

### Post by mountainman101 on 2007-04-14
I came to the same conclusions myself.  The actual problems was fonts-base.  Once I installed that, Xwindows started, but never got passed the initial load screen.  I said the Heck with it and installed the desktop version, which I am typing this from, so works good. Thanks all!

---

