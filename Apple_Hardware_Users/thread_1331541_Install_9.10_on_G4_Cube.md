---
title: "Install 9.10 on G4 Cube"
date: 2009-11-19
forum: Apple Hardware Users
---

### Post by avtolle on 2009-11-19
I have been successful in installing 9.10 on a G4 Cube using the procedure that follow. 

First, download the Alternate CD iso and burn to disk.

Second, elected to install a cli only version by inputting "cli-powerpc" at the yaboot 'boot' prompt (without the quotes, of course).

Third, once installed, and after a restart, sign in and ```
sudo aptitude update
sudo aptitude safe-upgrade
```to get all updates.

Fourth, at the 'terminal prompt' once the updates are installed, ```
cd /etc/X11 #change directory
sudo nano xorg.conf #open a blank file to input correct parameters for system
```In my xorg.conf file (located in the directory /etc/X11)  I put the following information for my system, which has an ATI 128 Rage PF/PRO AGP 4x TMDS video card, and a 15" Apple Studio Monitor (carefully note where quotation marks are and are not used):> 
Section "Device"
            Identifier        "Configured Video Device"
            Driver             "fbdev"
            BusID             "PCI:0:16:0"
            Option             "UseFBDev"           "true"
EndSection

Section "Monitor"
            Identifier        "Configured Monitor"
            Horizsync       28.0-49.0
            Vertrefresh     60
EndSection

Section "Screen"
            Identifier        "Default Screen"
            Defaultdepth    24
            SubSection "Display"
                         Depth   24
                         Modes             "1024x768@60"     "800x600@60"     "600x480@60"
            EndSubSection
            Monitor              "Configured Monitor"
            Device                "Configured Video Device"
EndSection   
Then, ^o to write the file, and ^x to exit nano.

Fifth, at the command line prompt, I input ```
sudo aptitude install ubuntu-desktop
```as I wanted a full fledged Gnome environment, but at this point the user may install the desktop or window manager desired, e.g. icewm, lxde, etc., along with such configuration files needed or desired.

Sixth, once all is installed, cleaned up, etc., then **I** restart from the command line prompt ```
sudo restart now -r
```Seventh, at the second yaboot prompt (Boot), select the default (which is Linux for a single os system); **do not** pass the kernel parameter *video=ofonly*, as on subject system, this causes the display to "go haywire", becoming unusable. This parameter is also not present in the base /etc/yaboot.conf file.

Standard disclaimer: the above works on a G4 Cube, 576 MB RAM, with a 15" Apple Studio Monitor, Rage 128 PF/PRO video card. Different system? Different parameters will be needed for video card, etc. 

Good luck.

---

