---
title: "ATI DRI &amp; Beryl"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by mgh88 on 2006-11-08
Hi 
I am getting this error message after i have installed the ATI fglrx 
when i do fglrxinfo

[COLOR="Red"]driverXlib:  extension "XFree86-DRI" missing on display ":0.0".[/COLOR]
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I have installed beryl but it doesn't work and i think this is the reason.
I have a radeon 9550 graphics card

Any help?

---

### Post by MasterOfDisaster on 2006-11-08
On XGL, DRI will always appear to be disabled, and is the reason OpenGL games do not work.  In AIGLX, DRI appears enabled.  Are you using XGL or AIGLX?

---

### Post by mgh88 on 2006-11-08
I am using XGL.  But when i am using XGL i don't get a beryl splash screen or anything.  I get the emerald in the task bar but it doesn't affect anything

---

### Post by MasterOfDisaster on 2006-11-08
Try executing beryl-manager in a terminal to see what error messages come up.

---

### Post by mgh88 on 2006-11-09
When i type beryl-manager in the terminal my screen flickers then i get nothing all my windows disappear and my taskbars just go blank i can't do anything.

---

### Post by manno on 2006-11-10
I also have a 9550 and I can't get my openGL Drivers to work, though I had no problems with my 9600

UPDATE!!!

Found this informationworked for me, I used method 2!!

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.30.3_drivers_in_Ubuntu_Edgy_Manually")

blatant copy & paste follows:
________________________________________________________________________________

Method 2: Generating/Installing Ubuntu packages for the new 8.30.3 drivers in Ubuntu Edgy Manually

The new fglrx driver supports Radeon 9500+ (older cards will not work!) and the X-series cards up to X1900.
[edit]
Disable Composite Extension

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to to disable Composite you have to edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

[edit]
Blacklist old fglrx module from linux-restricted-modules

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.28.8), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

sudo gedit /etc/default/linux-restricted-modules-common

Edit DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

[edit]
Installing the new driver

Download the ATI driver installer: ati-driver-installer-8.30.3.run (this installer is for 32bit and 64bit systems)

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

Create .deb packages:

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.30.3.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

Install .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.30.3-1*.deb
sudo dpkg -i fglrx-kernel-source_8.30.3-1*.deb
sudo dpkg -i fglrx-control_8.30.3-1*.deb

Remove any old fglrx debs from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Compile the kernel module:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

IMPORTANT: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Note: You could also edit your /etc/X11/xorg.conf file to change your driver to fglrx then run:

sudo aticonfig --overlay-type=Xv

This way your xorg.conf file will stay clean.

Now Reboot:

sudo shutdown -r now

[edit]
Confirm that it worked

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.6119 (8.30.3)

$ glxinfo | grep render
direct rendering: Yes

If your direct rendering is disabled, you may have to symlink the dri folder:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/

---

