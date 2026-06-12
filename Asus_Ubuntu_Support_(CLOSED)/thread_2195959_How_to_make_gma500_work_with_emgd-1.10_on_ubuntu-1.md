---
title: "How to make gma500 work with emgd-1.10 on ubuntu-12.04 with MATE desktop."
date: 2013-12-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by validust on 2013-12-27
My machine is ASUS 1101HA. I started this procedure using PCLinuxOS-2.6.33...etc,
    but any OS will do, though preferably with the "partimage" software.

    Download and install ubuntu-12.04.4 (or .5):  [http://releases.ubuntu.com/12.04.5/](http://releases.ubuntu.com/12.04.5/) 
    into a 10GB ext3 partition.
    Install synaptic and gdebi.
    Install gdm. Install kernel 3.2.0-49-generic-pae (from repository). *Image and headers.*
    In /etc/modprobe.d/blacklist.conf,  blacklist poulsbo, psb_gfx, and gma500_gfx.

    Download and install MATE Desktop: [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)
    Reboot with kernel 3.2.0-49.
    Choose "MATE" when logging in. The display will be unresolutionable, as is meant.

  Here is where partimage is *very* useful. Use whichever OS you have, and make an 
image (a .000 file) of the ubuntu-12.04 partition. This will save you from having 
to do it all again, if the next step turns into a totally confusing chaos. 
Encouraging, isn´t it!

Unmark precise´s repositories.

Download oneirics xserver-xorg.core 1.10.4, and xserver-common 1.10.4
[https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-core/2:1.10.4-1ubuntu4](https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-core/2:1.10.4-1ubuntu4)
[https://launchpad.net/ubuntu/oneiric/i386/xserver-common/2:1.10.4-1ubuntu4](https://launchpad.net/ubuntu/oneiric/i386/xserver-common/2:1.10.4-1ubuntu4)

Download the following versions:
    libutouch-evemu1_1.0.9-0ubuntu1_i386.deb
    libutouch-frame1_2.2.3-0ubuntu1_i386.deb
    libutouch-grail1_3.0.5-0ubuntu1_i386.deb
xserver-xorg-input-evdev   [https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-evdev/1:2.6.0-1ubuntu13](https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-evdev/1:2.6.0-1ubuntu13)
xserver-xorg-input-mouse   [https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-mouse/1:1.7.1-1](https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-mouse/1:1.7.1-1)
xserver-xorg-input-synaptics   [https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-synaptics/1.4.1-1ubuntu2](https://launchpad.net/ubuntu/precise/i386/xserver-xorg-input-synaptics/1.4.1-1ubuntu2)
xserver-xorg-input-wacom   [https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-input-wacom/1:0.11.0-0ubuntu2](https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-input-wacom/1:0.11.0-0ubuntu2) , and
xserver-xorg-video-fbdev   [https://launchpad.net/ubuntu/natty/i386/xserver-xorg-video-fbdev/1:0.4.2-3ubuntu6](https://launchpad.net/ubuntu/natty/i386/xserver-xorg-video-fbdev/1:0.4.2-3ubuntu6)
xserver-xorg-video-vesa   [https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-video-vesa/1:2.3.0-7](https://launchpad.net/ubuntu/oneiric/i386/xserver-xorg-video-vesa/1:2.3.0-7)

Remove precise´s xserver-xorg-core and xserver-common (which are lts-trusty). Doing so 
will remove a number of other xservers.
Install the above downloaded packages, using gdebi. Pin them.
Mark again, and reload precise´s repositories.

  Download the emgd-110 repository (Yes, the dot is gone.) by adding to 
synaptic:
<deb [http://ppa.launchpad.net/gma500/emgd110/ubuntu](http://ppa.launchpad.net/gma500/emgd110/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/gma500/emgd110/ubuntu](http://ppa.launchpad.net/gma500/emgd110/ubuntu) oneiric main>. Reload.

  Hooray for launchpad!

Reboot.

  Install the packages. First xorg-emgd. There are more than twenty of them, and not all are named 110. 
Installing "emgd-support" brings along all of them.
Reboot.
  Didn´t work? - Be glad, then, that you have let partimage make a .000 file, to try
again!

  One thing did not function well. The pointer was inordinatly slow even at the 
highest speed. I wish I remembered who solved that problem, and in which forum or 
site, so credit could be given. Sorry and thank you! 
  Write "synclient MinSpeed=1.6 && synclient MaxSpeed=1.8 && AccelFactor=0.18" 
in a root terminal, press ENTER and try it out. The values can be 
changed to your liking, of course.
You can make this a start-up application, named whizz. :D
   Also a wee hiccup re sound, the remedy of which ought to be satisfactory since
i had forgotten it: It seemed that pulseaudio interfered with streaming, so that
there was sometimes no sound and sometimes a doubling of the sound, ound.
- Quite disorienting, audially. I removed all pulseaudio packages, except for libpulse0
and libpulse-mainloop-glib0. Alsa rules! 

  I have found two of ubuntu-12.04´s kernels that accept this whatchamacallit; 
3.2.0-26-generic and 3.2.0-49-generic-pae.
It works amazingly well. xv in mplayer (mplayer2 with smplayer), without any 
problems. I´ve yet to find a video format that doesn´t play perfectly. Though
1080p is too much for my machine. Most 720p videos play fine, if it doesn´t
use the full display - 16:9. 
Having composite effects is not at all necessary, but it´s *nice*. - Writing 
the start-up application "marco --composite" gives that, without any 
noticeable slowing down of anything.
    
  And I have not found one single mention of this or any alike solution to the 
infamous gma500´s infamy. Hence this try-to how-to. Good luck!

--- Most of the above was edited (and simplified, yup) 13 aug 2014. ---


-----------------------------
Adding this 3 feb 2014

   After having used this well-behaving bastard some four months, I discovered that when rousing it from suspend mode, the given brightness values were lost. When wooing Power Management, there was no response.
   That is not a problem to me, obviously, but for whomever it is so, here is a way to get around it.  
Write in a terminal: "sudo setpci -s "00:02.0" F4.B=45" (No outer quotation marks.) and press ENTER. The value "B=45" can be changed - to "B=40", for instance.

   Hmm... Come to think of it, I was rather tired of having to write password for this and that again and again. After some experimenting, this is how I escaped that irritation:
Install gksu.
Open Caja (or whichever is your preferred file manager) as root.
Open /etc/sudoers   
Heed the hair raising warnings, or if you have another OS on another partition on the same hard disk, from which you can access this file as root, ignore them, and copy-and-paste the following lines (just a suggestion. And, of course, change "yourusername" to *your* user name):

yourusername   ALL= (root) NOPASSWD: /usr/sbin/gparted

yourusername   ALL= (root) NOPASSWD: /usr/sbin/synaptic
 
yourusername   ALL= (root) NOPASSWD: /usr/bin/caja

yourusername   ALL= (root) NOPASSWD: /usr/bin/x-terminal-emulator

yourusername   ALL= (root) NOPASSWD: /sbin/reboot

yourusername   ALL= (root) NOPASSWD: /sbin/poweroff

Then, right click the corresponding launcher, let´s say GParted, open "properties", and write "gksu /usr/sbin/gparted" there (no quotation marks). Most important is that you give your file managers launcher its correct command - "gksu" (no quotation marks),  followed by the same command that you have pasted or written in the sudoers file.

A warning: If you share your computer with NSA  (Non Savoury Associates), DO NOT DO THE ABOVE. There *is* a very sound reason for the existence of the password.

---

