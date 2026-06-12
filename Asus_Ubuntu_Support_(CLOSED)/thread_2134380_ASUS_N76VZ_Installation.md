---
title: "ASUS N76VZ Installation"
date: 2013-04-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thomi_ch on 2013-04-11
Hey all

In the thread [http://ubuntuforums.org/showthread.php?t=1992461&page=2&p=12597268#post12597268](http://ubuntuforums.org/showthread.php?t=1992461&page=2&p=12597268#post12597268) i wrote some information about ASUS n76VZ and boot LiveCD/LiveUSB/LiveDVD variants of, i think, any (?)ubuntu.

This thread should help other N76VZ users to get it running. I will update this post with latest information, so instructions are always on top!

Notebook Type: ASUS N76VZ, 256GB SSD, 750GB HD, 16GB Memory
Info: [http://www.asus.com/Notebooks_Ultrabooks/N76VZ/#specifications](http://www.asus.com/Notebooks_Ultrabooks/N76VZ/#specifications)

**Installation from LiveUSB/LiveCD/LiveDVD**
Pre-Requirements:
Bios have to be prepared to start LiveSystem.
. enter Bios: Start Notebook, press ESC until boot menu appears and then choose "Enter Setup"
. disable Secure Boot: Bios / Security / Secure Boot Control (at bottom)
. enable CSM: Bios / Boot / Launch CSM
. switch to IDE instead of AHCI mode: Bios / Advanced / SATA Configuration / SATA Mode Selection

Boot LiveSystem (my choice is Kubuntu 12.10 or current 13.04) and choose "Try Kubuntu".
Now you need to rewrite partition table on SSD and HDD with partitionmanager
. start konsole and run: sudo partitionmanager
. right click the SDD 256GB and select "New Partition Table" and apply the new partition table
. do same on the 750GB HD

Now you can install kubuntu and choose the 256GB SSD as installation destination... I do so, cause i use the 750GB for all data...
In my situation, after 5-10 min, system successfully installed ;)...

If you connected wired LAN you will see, that install wizard can't get a connection, cause the device could not loaded.. no prob, just install and later do a WLAN connection and make all the updates, then the LAN device come available.
Be informed, i do always install Kubuntu PPA ([https://launchpad.net/~kubuntu-ppa](https://launchpad.net/~kubuntu-ppa)) and Kubuntu PPA Backports ([https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)), cause i want to be up to date ;) and also have latest KDE...

**Configuration**
*Back lights and Touchpad*
While notebook start you see the beautiful keyboard back light ;).. but after installation Fn+F3/F4 and also Fn+F9 doesn't work.. 
Now a nice guy made a KDE app with some scripts, that will control KB and LCD backlight:
[ASUS Toolbox OSD]("http://kde-apps.org/content/show.php?content=157204")

*Graphiccard*
As i understand, there are two Graphiccards: Intel which is direct connected to the Notebook LCD and Nvidia GT650M which is used for external ports like the HDMI.
The nvidia card also can be used for rendering, do all the work and send it to Intel's buffer which will show the result on the Notebook LCD. For this, Bumblebee is used:
[http://bumblebee-project.org/install.html#Ubuntu](http://bumblebee-project.org/install.html#Ubuntu)
Just install Bumblebee as described and Notebook LCD is running perfectly ;)...

Seams that current external HDMI isn't easy supported, read this:
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup)
Read "Wiring" paragraph...

What i know now is, that bumblebee default behavior is to render on Nvidia and send the data to Intel's buffer for displaying on Notebook LCD.
You can check that with following commands:
glxspheres
Polygons in scene: 62464
Visual ID of window: 0xc4
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
60.068722 frames/sec - 67.036694 Mpixels/sec
59.906141 frames/sec - 66.855253 Mpixels/sec
....

..or the same with optirun to see frames/sec with nvidia:
optirun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 650M/PCIe/SSE2
178.767904 frames/sec - 199.504981 Mpixels/sec
167.170307 frames/sec - 186.562063 Mpixels/sec
...

I also have enabled nvidia_313 driver with jockey-text:
sudo jockey-text -e kmod:nvidia_313_updates


For X there are two instances running:
/usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
Xorg :8 -config /etc/bumblebee/xorg.conf.nvidia -sharevts -nolisten tcp -noreset -verbose 3 -isolateDevice PCI:01:00:0 -modulepath /usr/lib/nvidia-experimental-310/xorg,/usr/lib/xorg/modules

First seams to be the Intel card, which is direct connected to the Notebook LCD and the second is the Nvidia card.
There are new drivers comming from Nvidia and also new Kernels for supporting all the new features.. we have to wait..
For the moment i connected my external monitor over VGA port and this works out of the box, cause VGA port is connected to the Intel card.


*Subwoofer*
Source: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808/comments/34]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808/comments/34")
Yes, another thing.. enable ASUS Subwoofer control, simple and easy:
sudo vi /etc/modprobe.d/alsa-base.conf

Add following lines at the end of the file:
# Enable ASUS Subwoofer
options snd-hda-intel model=asus-mode4

Reboot system and you got a subwoofer control (Bass-Speaker) in alsamixer...


Cheers
thomi

---

### Post by thomi_ch on 2013-04-29
About running X instances, this are only available, if you do the following steps from [Bumblebee Multi-Monitor Setup]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup").
> Edit /etc/bumblebee/bumblebee.conf and change PmMethod=auto to PmMethod=none (twice).
In /etc/bumblebee/bumblebee.conf, change KeepUnusedXServer=false to KeepUnusedXServer=true. Remove the UseEDID and Option "AutoAddDevices" "false" lines in /etc/bumblebee/xorg.conf.nvidia. Trigger a start of the X server with optirun true.

If you just install bumblebee with default settings, only the default X instance is running:
> /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none

thomi

---

### Post by thomi_ch on 2013-11-06
Hey all

Upgrading from 13.04 to 13.10 is... easy, but breaks nvidia, bumblebee installation.
You can start your machine, but after entering password and press enter, xserver restart with: Segmentation fault at address 0x88 ([http://paste.ubuntu.com/6373686/](http://paste.ubuntu.com/6373686/))

What to do, to get it back?

Login over ssh to your machine, o even boot from a live cd.. cause in my situation CTRA+ALT+F1 doesn't work :(

Now you have to reinstall installed nvidia drivers and also bumblebee-nvidia, check out next link for install instruction:
[https://wiki.ubuntu.com/Bumblebee#Basic_Setup](https://wiki.ubuntu.com/Bumblebee#Basic_Setup)

Checkout installed packages with:
dpkg -l | grep nvidia
dpkg -l | grep bumblebee

You also can remove all installed packages from nvidia and bumblebee and reinstall eg directly nvidia-319 and bumblebee-nvida...

No, before restart, you have to update /etc/bumblebee/bumblebee.conf, check out here:
[https://wiki.ubuntu.com/Bumblebee#Updating_drivers](https://wiki.ubuntu.com/Bumblebee#Updating_drivers)

After this changes, restart your machine and you can login.. but no effects are there. :(

:) Just read here [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting#3d-effects-dont-work-and-when-running-3d-apps-in-a-terminal-you-get-xlib-extension-glx-missing-on-display-0](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting#3d-effects-dont-work-and-when-running-3d-apps-in-a-terminal-you-get-xlib-extension-glx-missing-on-display-0)
and: sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core

That's it.. with above steps, i got my machine back...

regards
thomi

---

