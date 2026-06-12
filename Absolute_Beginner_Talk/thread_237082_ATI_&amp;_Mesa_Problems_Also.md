---
title: "ATI &amp; Mesa Problems Also"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by raggit on 2006-08-15
I know there are threads out there and I've been reading them for 3 days and I either have X errors and have to go back to the origional xorg.conf or when i do a fglrxinfo i see the mesa drivers.

I feel as if I've gone through all the tutorials to make it happen correctly , i used the 2nd one on the most popular how to...Don't have link right off hand.

So if you guys that have seen this type of thread a million and 1 times feel like assisting yet another NOOBUNTU please feel free.

I'll be glad to give you any info I have>

ati radeon 7500 is my card.  I'm on a Thinkpad t41

---

### Post by =Kevin= on 2006-08-15
Heya, try this one:

Terminal:
sudo gedit /etc/default/linux-restricted-modules-common

Now find this DISABLED_MODULES=""
Replace it with DISABLED_MODULES="fglrx"

Terminal again:
wget [http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run)
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.27.10-x86.run
./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.27.10-1_i386.deb
sudo dpkg -i fglrx-control_8.27.10-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

And then reboot, you're done!
Note,if you want to know what all these commands do, check
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

I only gave the commands to insert into the terminal.

---

### Post by raggit on 2006-08-15
After following those directions & the reboot I went to the terminal and typed the command

fglrx

and was confronted with 

```
mark@ubuntu-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by chuckao on 2006-08-16
> **raggit said:**
> After following those directions & the reboot I went to the terminal and typed the command

fglrx

and was confronted with 

```
mark@ubuntu-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Hi,

Did you install linux-headers package? You need the the kernel headers to install ATI driver.

And, check the installation results in /usr/share/fglrx/fglrx-install.log 

cheers,

---

### Post by raggit on 2006-08-16
I think one of the problems i may be having is that I have the 
mobility m7 7500.  Are there solutions for this?

---

### Post by powder on 2006-08-16
Your card is not supported by the current fglrx driver.  From ATI's FAQ:

> Which ATI graphics cards can use this driver?

The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as FireGL 8700 and later products. We do not currently plan to include support for any products earlier than this. Drivers for earlier products should already be available from the DRI Project or Utah-GLX project.

---

### Post by gustl87 on 2006-08-16
hello !

i use the older ati chip (mobility m6) with the normal open source driver called "radeon" in the xorg.conf

open gl is working fine except some strange image errors during just very few applications.

so try the "radeon" driver.

but your system might freez sometimes as it does with mine.

if it freezes you have to modify your xorg.conf as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

i got this from here :

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

#sorry for my bad english.

---

