---
title: "Need help with Graphics Card and Wireless Card"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by tsav87 on 2007-03-15
I have an nVidea GeForce Go 7900 GS and I am not sure what kind of Wireless Card I have, but I do know it;s and Intel.

How do I install the driver for the Graphics Card and how do I find out what kind of wireless card I have and then how can I install the driver for it?

TIA

BTW, I have dedicated my personal laptop to Ubuntu :)

---

### Post by Ashrael on 2007-03-15
well the video driver is easy, the newest can be found here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

the wificard might not be that easy, i really don't know...I don't know how apt you are with linux/ubuntu but you might consider buying one that is supported out of the box...

hope this helps....
keep us posted...

ashrael

---

### Post by overdrank on 2007-03-15
> **tsav87 said:**
> I have an nVidea GeForce Go 7900 GS and I am not sure what kind of Wireless Card I have, but I do know it;s and Intel.

How do I install the driver for the Graphics Card and how do I find out what kind of wireless card I have and then how can I install the driver for it?

TIA

BTW, I have dedicated my personal laptop to Ubuntu :)

Hi if you want to find your internet card it go to terminal and type *lspci* and it will list your components.

---

### Post by John.Michael.Kane on 2007-03-15
To install your nvidia drivers using edgy 6.10.

Run:
```
gksudo aptitude install linux-generic
```

Now install the gpu driver:
```
gksudo aptitude install nvidia-glx
```

Enable the driver in your xorg:
```
gksudo nvidia-xconfig
```

Nex step:
```
gksudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Paste the following
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```

Last step:
press CTRL+ALT+BACKSPACE 

Note if you need to reset your xorg:

Run:
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tsav87 on 2007-03-15
Cool, i got the driver isntalled for the Graphics Card.

Here is the output for the lspci
```
travis@travis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0298 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

---

### Post by John.Michael.Kane on 2007-03-15
Your wifi-->0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)  is seen looking at the lspci output.

Does networkmanager show it as receiving a signal?
Aslo does it show up under System-Administration-Networking?

Most likely you will have to fill out the wpa info ssid ect. 

You will have to wait for someone with a little more insight on that as i don't run wifi.

---

### Post by tsav87 on 2007-03-15
No, it does not show that it is receiving a signal, but it does show up in the network manager.

---

### Post by tsav87 on 2007-03-16
Bump

---

### Post by tsav87 on 2007-03-16
I figured out the wireless card :D

For some reason, my router wasn't assigning a IP address, so I assigned one for it.

Under connection settings, I changed the configuration from Automatic Configuration  to Static IP.

Then I assigned an IP Address, 
Then I set up the Subnet mask to 
Then I set the Gateway Pass to , which is the address I use to configure my router.

Woot!!!

---

