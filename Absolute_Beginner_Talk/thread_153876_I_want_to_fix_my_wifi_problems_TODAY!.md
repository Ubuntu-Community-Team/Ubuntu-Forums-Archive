---
title: "I want to fix my wifi problems TODAY!"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Xitanto on 2006-04-01
Right.

```
xitanto@ubuntu:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

xitanto@ubuntu:~$

```

Results for nDiswrapper -l:

```
xitanto@ubuntu:~$ sudo -s
root@ubuntu:~# ndiswrapper -l
Installed ndis drivers:
bcmw15  invalid driver!
bcmwl5  driver present, hardware present
bcwl5a  invalid driver!
netani  driver present
tmimo3p driver present
root@ubuntu:~#

```

That above shows driver present, hardware present on one of my wireless recievers (I have two on this computer - a card in the cardbus and a built-in 802.11g reciever). The one that is being recognised is the built-in one.

Results from lspci:

```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 04)0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:05:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:05:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
root@ubuntu:~#

```

Now, how do I get onto the net via my wireless connection? My setup:

SSID: stopwardriving
No security keys required.
MAC address restricted to my card & the inbuilt reciever - should be recognised by the router.

I've been trying to follow tons of tutorials on this and other ubuntu linux forums/blogs and as a result I can not connect to the net via wifi & I have a whole bunch of changes to system config files. I just want to know what I'm supposed to do past this point. ](*,)

---

### Post by jshein on 2006-04-01
Is this on a laptop? If so, then what make & model?

I have found that there are different procedures for different laptops.

---

### Post by Xitanto on 2006-04-01
[QUOTE=jshein]Is this on a laptop? If so, then what make & model?

I have found that there are different procedures for different laptops.[/QUOTE]

I have an acer aspire 3600 notebook. =/ No, I haven't been able to find any procedures on the net for this notebook.

Thanks for this, by the way. :-D

---

### Post by Xitanto on 2006-04-01
Sorry about the double post, but I am still having trouble with this...

---

### Post by jshein on 2006-04-02
ok. I am running an Acer TravelMate 4400, with a turion64 CPU. Running 32 bit Breezy, i686 kernel.

I just went through the frustration of getting this to work. This may be a long winded explanation, but I now have it working properly, after all other methods posted failed.

Here is what I would suggest.

1: Check the outplut of lspci. If it has any "unknown" entries, the you should update your pci.ids file. This file is an index of sorts that the kernel references for installed hardware. An updated file can be downloaded from:
[http://pciids.sourceforge.net](http://pciids.sourceforge.net)

To update it, First back up the old one

**#sudo cp /var/lib/misc/pci.ids /var/lib/misc/pci.ids.OLD**

Then copy the downloaded file over the existing one.

**#sudo cp <path to downloaded file> /var/lib/misc/pci.ids**

*_You will now need to reboot your pc if you have updated this file._*

2: Next you will probably need the acer_acpi package. You can downloaded it from:
[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

Compile it as follows:

[B]#tar zxvf acer_acpi-0.3.tar.gz
#cd acer_acpi-0.3
#make
#sudo make install
#sudo modprobe acer_acpi[/B]

Then check the output of dmesg for errors.
**#dmesg | grep acer**

I have attached my own precompiled driver, for i686 2.6.12-10 if you are running this kernel. 
You would install this with
[B]#sudo make install
#sudo modprobe acer_acpi[/B]

For my installation I had to then install the latest ndiswrapper, which meant removing the breezy restriced-modules. You may have different results.

To enable the wireless you input the following:
**#sudo echo "enabled : 1">/proc/acpi/acer/wireless**

Then configure your wireless connection normally.

I run the following script, placed in /usr/bin/acerwl to enable my wireless connection, and start networking. the script is modified from the original version to suit Ubuntu. The script needs to be run as root, so I edited the following using visudo
**#sudo visudo**

add the following line at the bottom
*%users	ALL=(ALL)	NOPASSWD: /usr/bin/acerwl*

Run the script using sudo
**#sudo /usr/bin/acerwl**

--script--

#!/bin/bash
#
# Copyright Francois Wautier 2005
# A script tp toggle the wireless adapter on Acer 5020 Series laptop 
# This script is provided as-is, without any warranty.
# Permission is granted to use and abuse this script as
# long as the original copyright is mentioned
#
# Interface to use
interf=wlan0
#
# Module to us
wmodule=ndiswrapper
#
#
isloaded=`lsmod|awk '{ print $1 }'|grep $wmodule`
#
acerok=`lsmod|awk '{ print $1 }'|grep acer_acpi`

if [ "$acerok" == "" ]; then
	echo "acer_acpi not loaded. Attempting to load"
	/sbin/modprobe acer_acpi
	/sbin/modprobe acer_acpi
fi

acerok=`lsmod|awk '{ print $1 }'|grep acer_acpi`
if [ "$acerok" == "" ]; then
  	echo "Could not load acer_acpi. Aborting"
	exit
fi


if [ "$isloaded" == "" ]; then
	#Load it
	# Enable the radio
	echo "enabled : 1" >/proc/acpi/acer/wireless
	sleep 1
	# Load the driver. Hotplug should do the rest
	/sbin/modprobe ndiswrapper
	sleep 1
        /sbin/ifup wlan0
else
	/sbin/ifconfig $interf down
	#/etc/init.d/net.$interf stop
	echo "enabled : 0" >/proc/acpi/acer/wireless	
	/sbin/rmmod ndiswrapper
fi

--end of script--

Good luck. Let me know if you have any problems. I may have missed something.

---

### Post by Xitanto on 2006-04-02
After I updated the pci.ids file my ethernet stops working. I can't get the internet any more. :S

Reverted back to old pci.ids file and it's still screwed. Any suggestions?

---

### Post by jshein on 2006-04-02
First of all did you reboot after updating the pci.ids file?

Second.

This is my network config file, located at /etc/network/interfaces. You can manually edit this file or use the KDE/Gnome utility to configure your network.


--/etc/network/interfaces--
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep

# The primary network interface

iface wlan0 inet dhcp
wireless-essid <ssid goes here>
wireless-key <key goes here in the format a1:b2:c3 etc >

--end of file--

I hope this helps.

---

### Post by Xitanto on 2006-04-02
[QUOTE=jshein]First of all did you reboot after updating the pci.ids file?

Second.

This is my network config file, located at /etc/network/interfaces. You can manually edit this file or use the KDE/Gnome utility to configure your network.


--/etc/network/interfaces--
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep

# The primary network interface

iface wlan0 inet dhcp
wireless-essid <ssid goes here>
wireless-key <key goes here in the format a1:b2:c3 etc >

--end of file--

I hope this helps.[/QUOTE]

Yes, I rebooted. Hang on a sec, I'll go edit the network file.

---

### Post by Xitanto on 2006-04-02
**I am now locked out of my Ethernet connection.**

Could someone please explain the results of my ifup wlan0?

I'm getting something along the lines of:

Can't read "/etc/network/interfaces" file. Wrong line somewhere.

My USB drive won't boot any more, so I can't get you a good copy of the terminal's error. Sorry about this.

Any way I can fix this mess?

---

### Post by jshein on 2006-04-02
What is the output of lspci? Are there any "unknown" entries or has everything been identified?

One thing to try is to wipe all configuration data out of the network/interfaces file, and start fresh, using the gnome or kde configuration tools. You will have to configure your eth0 and wlan0 interfaces.

So all that would be in that file is:

--/etc/network/interfaces--

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep

# The primary network interface

--end of file--

---

### Post by xXx 0wn3d xXx on 2006-04-02
Try using [ this tutorial ](http://ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom+chipsets) This got my Broadcom card to work and it's very easy to follow.

---

### Post by jshein on 2006-04-02
Unfortunately, that tutorial did not work with my Acer laptop, and most other Acer units due to the fact that you need the acer_acpi modules installed in order to turn the wireless card on.

Without it installed, ndiswrapper will show that the drivers are present and hardware is present. It just will not work without acer_acpi.

---

### Post by nocturn on 2006-04-03
[QUOTE=jshein]Unfortunately, that tutorial did not work with my Acer laptop, and most other Acer units due to the fact that you need the acer_acpi modules installed in order to turn the wireless card on.

Without it installed, ndiswrapper will show that the drivers are present and hardware is present. It just will not work without acer_acpi.[/QUOTE]

I guess this is because the built-in antenna is turned off by default, I read about this several times.

Some people reported that turning on the Antenna in Windows and soft-rebooting got their network running, not permanently though.

So, in the end you really need the acer_acpi drivers...

---

### Post by bloodniece on 2006-12-22
This worked perfectly for my TravelMate 4400.  THANKS!!!!! :D

---

