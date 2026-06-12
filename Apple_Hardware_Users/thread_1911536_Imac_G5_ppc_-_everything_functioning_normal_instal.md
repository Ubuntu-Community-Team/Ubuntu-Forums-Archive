---
title: "Imac G5 ppc - everything functioning normal installing from 18/01/2012 alternate cd"
date: 2012-01-19
forum: Apple Hardware Users
---

### Post by allebone on 2012-01-19
Imac G5 ppc - everything functioning normal installing from 18/01/2012 alternate cd build (12.04 precise pangolin)

Unity was not functional, but installing xfce4 and gnome then using gnome as the desktop from the login screen fixed the fan speed issue. 

Power management etc all seems normal and can do everything from the gnome session that I need. 

Occasionally a crash report appears and you can click send but other than that nothing appears to break/stop functioning.

Had no installation issues so far, using as an ssh and fileserver at the moment without any problems.

If anyone needs help or had any other experiance installing let me know, as far as I can tell it all works once you get out of unity and use some other display manager - you can switch to gdm if you like but leaving it on lightdm also works.

Pete

---

### Post by allebone on 2012-01-19
Commands used once base install is done (from terminal)

sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot

sudo apt-get install xfce4 xfce4-goodies xfprint4

during "select window manager question" either gdm or lightdm 
work equally well.

sudo apt-get install gnome-shell gnome-desktop-environment

From login screen change to gnome classic with no effects

Ubuntu functions normally when logging in.

---

### Post by Nato71 on 2012-05-18
Hi Allebone, glad to hear your install was ok. I'm trying to install kubuntu 12.04 ppc on my iMac g5 but have two problems.
1. The fan is on full speed all of the time. Grrr!
2. I am booting from the live cd and when I try to install it to the partitioned HDD it says I don't have permission, config may be broken.

Any advice please?

Thanks

---

### Post by allebone on 2012-05-19
> **Nato71 said:**
> Hi Allebone, glad to hear your install was ok. I'm trying to install kubuntu 12.04 ppc on my iMac g5 but have two problems.
1. The fan is on full speed all of the time. Grrr!
2. I am booting from the live cd and when I try to install it to the partitioned HDD it says I don't have permission, config may be broken.

Any advice please?

Thanks
Yes I had the same issue, on Ubuntu. I needed to use the alternate install disc. Additionally changing from unity (in my case) to gdm solved rhe issue, because once the proc is used, the fans go mad. Using 3d effects always caused processor usage to be high, so this in turn made the fans always spin. 

For the partitioning did you make a newworld boot partition on the drive? If you can get it installed, and booting without the cd then you can move on to fixing the fans. Alternatively you could install ubuntu and then change the installation to a kubuntu one by installing the relevant packages once installed.  

What plan would you like to take?

Pete

---

### Post by Nato71 on 2012-05-19
Thanks for getting back to me so quickly. I will look at fixing the fans once it is installed.

Yes I did new world, root and spare partitions and now the installation has begun but hangs at 64% when loading the usb-storage for USB storage module. I can still use the live session while this is happening but it will not progress.

I should say that I am dual booting with OSX 10.4.11 and had tried unsuccessfully to get Ubuntu to work either!

I will download the alternate cd to see if that makes a difference.

Thanks again, very much appreciated.

Nato

---

### Post by rsavage on 2012-05-19
Fans: Make sure you have the correct module loaded....
 
Use the command lsmod or look in your logs.
 
The following info is taken from the comments at the top of the source files. If you want more details about each module then use the command 'modinfo'. e.g. modinfo therm_pm72 
 
therm_pm72
 
* Device driver for the thermostats & fan controller of the 
* Apple G5 "PowerMac7,2" desktop machines.
 
windfarm_pm112 
 
* Windfarm PowerMac thermal control. 
* Control loops for machines with SMU and PPC970MP processors. 
 
windfarm_pm121 
 
* Windfarm PowerMac thermal control. iMac G5 iSight 
 
windfarm_pm81 
 
* Windfarm PowerMac thermal control. iMac G5 
 
windfarm_pm91 
 
* Windfarm PowerMac thermal control. SMU based 1 CPU desktop control loops 
 
therm_windtunnel 
 
* The G4 "windtunnel" has a single fan controlled by an 
* ADM1030 fan controller and a DS1775 thermostat. 
* WARNING: This driver has only been testen on Apple's 
* 1.25 MHz Dual G4 (March 03). It is tuned for a CPU 
* temperature around 57 C. 
 
therm_adt746x 
 
* Device driver for the i2c thermostat found on the iBook G4, Albook G4

---

### Post by Nato71 on 2012-05-19
Awesome! Thanks for that

---

### Post by lprofil on 2012-06-16
Hey,

i got a 20' iMac G5 PPC which has the same fan issue under Ubuntu 12.04. Could you be more verbose on your comments on how to calm
the fans please?

Cheers
/lprofil

---

