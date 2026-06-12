---
title: "Why should I be root to download pictures from my camera ??"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-05
Why should I be root to download pictures from my camera ??
  (I use DIGIKAM to download)
  
How did you fix it ??
   
I have a canon Powershot A75 (installed & fully working)
  
Thank you & Greetings !!

---

### Post by louis_nichols on 2006-05-05
What method are you using to download images? Is it xsane, or does it appear as a USB mass storage device? What command are you issuing that tells you it needs root privileges?

---

### Post by patrick295767 on 2006-05-06
[QUOTE=louis_nichols]What method are you using to download images? Is it xsane, or does it appear as a USB mass storage device? What command are you issuing that tells you it needs root privileges?[/QUOTE]
  
It is not sane
  
I updated the libgphoto2, plugged my canon A75 camera, 
then run : 
gksudo digikam 
(same result with gthumb)
  
I then see the thumbnails of my photo I took
 
then, click on download and it works.
===
If I do it as user, the camera is like not detected... 
  
I dont know really how to fix this problem... 
  
Thank you for ur concern ! :-)

Pat'

---

### Post by louis_nichols on 2006-05-06
Unfortunatelly, I can not replicate your situation, as I don't have a camera like yours. I can only guess as to what is happening.

I would recommend you check out their [manual]("http://gphoto.sourceforge.net/doc/manual/") and especially [this section]("http://gphoto.sourceforge.net/doc/manual/permissions-usb.html") might help.

Otherwise, try asking on their [mailing list]("http://gphoto.sourceforge.net/mailinglists/").

I'm sure there is a solution somewhere, not too difficult. You have no reason to be mad at Ubuntu, or generally Linux, for this, since you are only experiencing a small downside of the security it offers.

---

### Post by patrick295767 on 2006-05-06
[QUOTE=louis_nichols]Unfortunatelly, I can not replicate your situation, as I don't have a camera like yours. I can only guess as to what is happening.

I would recommend you check out their [manual]("http://gphoto.sourceforge.net/doc/manual/") and especially [this section]("http://gphoto.sourceforge.net/doc/manual/permissions-usb.html") might help.

Otherwise, try asking on their [mailing list]("http://gphoto.sourceforge.net/mailinglists/").

I'm sure there is a solution somewhere, not too difficult. You have no reason to be mad at Ubuntu, or generally Linux, for this, since you are only experiencing a small downside of the security it offers.[/QUOTE]
  
Thank you very much !!
After some time, I will find the way ... just matter of patience ... 
  
Thx

Greetz

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=patrick295767]It is not sane
  
I updated the libgphoto2, plugged my canon A75 camera, 
then run : 
gksudo digikam 
(same result with gthumb)
  
I then see the thumbnails of my photo I took
 
then, click on download and it works.
===
If I do it as user, the camera is like not detected... 
  
I dont know really how to fix this problem... 
  
Thank you for ur concern ! :-)

Pat'[/QUOTE]
Patrick,

I have a Powershot A70 which is a very similar model.  I don't have any problem running digikam as a normal user.  These cameras do act as USB mass storage devices.  When the camera is plugged in, does "lsusb" detect it?  Does "dmsg" show a device node being created for it?

Are you using konqueror?  Can you reach it with a camera:// URL?

---

### Post by patrick295767 on 2006-05-06
strange ... 
we have no file like this in our distro ubuntu :  Add these lines to /etc/devfs.rules:

```
[usb_devices=10]
add path 'ugen*' mode 0660 group usb
add path 'da*s*' mode 0660 group usb
```

---

### Post by patrick295767 on 2006-05-06
I never saw such thing : 
celina@tower05:~$ lsusb
```
Bus 004 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
celina@tower05:~$ sudo su
Password:
root@tower05:/home/celina# lsusb
Bus 004 Device 007: ID 04a9:30b5 Canon, Inc.
Bus 004 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
root@tower05:/home/celina#
```
  
There is the error msg as normal user [here]("http://patrick295767.sitesled.com/fvwm/digikam.png")
  
   
   
  
Thank you !

---

### Post by louis_nichols on 2006-05-06
[QUOTE=patrick295767]strange ... 
we have no file like this in our distro ubuntu :  Add these lines to /etc/devfs.rules:

```
[usb_devices=10]
add path 'ugen*' mode 0660 group usb
add path 'da*s*' mode 0660 group usb
```[/QUOTE]

It's just one of those cases where the name and location of configuration files differs from distro to distro. It's in there somewhere, perhaps with another name...

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=patrick295767]I never saw such thing : 
celina@tower05:~$ lsusb
```
Bus 004 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
celina@tower05:~$ sudo su
Password:
root@tower05:/home/celina# lsusb
Bus 004 Device 007: ID 04a9:30b5 Canon, Inc.
Bus 004 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
root@tower05:/home/celina#
```
  
There is the error msg as normal user [here]("http://patrick295767.sitesled.com/fvwm/digikam.png")
  
   
   
  
Thank you ![/QUOTE]
Here is what I get:
```

carl@kepler ~ $ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04a9:3073 Canon, Inc. PowerShot A70 (ptp)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
It looks like there is a "Canon" line in your lsusb output on bus 4, device 7.  
```

$ dmesg
[4351242.279000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[4351374.863000] usb 3-2: USB disconnect, address 2

```
If you run "$ gphoto2 --auto-detect" from the terminal, does it find your camera?

---

### Post by patrick295767 on 2006-05-06
First, Thank you for your help!!  

dmesg & gphoto2 autodetect :
```
4294694.192000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r
edhat.com
[4294773.322000] Linux agpgart interface v0.101 (c) Dave Jones
[4294773.387000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[4294773.405000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294773.617000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294773.642000] shpchp: shpc_init : shpc_cap_offset == 0
[4294773.642000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294774.093000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 17 (level, low) -> I
RQ 17
[4294775.273000] gameport: EMU10K1 is pci0000:00:06.1/gameport0, io 0xec00, spee
d 1169kHz
[4294775.796000] irda_init()
[4294775.796000] NET: Registered protocol family 23
[4294777.745000] Floppy drive(s): fd0 is 1.44M
[4294777.760000] FDC 0 is a post-1991 82077
[4294778.197000] Real Time Clock Driver v1.12
[4294778.292000] input: PC Speaker
[4294778.769000] ts: Compaq touchscreen protocol output
[4294780.442000] NET: Registered protocol family 10
[4294780.442000] Disabled Privacy Extensions on device c02eb280(lo)
[4294780.442000] IPv6 over IPv4 tunneling driver
[4294781.378000] NET: Registered protocol family 17
[4294788.584000] ACPI: Power Button (FF) [PWRF]
[4294788.584000] ACPI: Power Button (CM) [PWRB]
[4294788.584000] ACPI: Sleep Button (CM) [SLPB]
[4294788.754000] ibm_acpi: ec object not found
[4294791.788000] eth0: no IPv6 routers present
[4294800.034000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[4294807.063000] kjournald starting.  Commit interval 5 seconds
[4294807.063000] EXT3-fs warning: mounting unchecked fs, running e2fsck is recom                          mended
[4294807.064000] EXT3 FS on hda5, internal journal
[4294807.064000] EXT3-fs: mounted filesystem with ordered data mode.
[4294807.247000] nfs warning: mount version older than kernel
[4312470.965000] nfs: server 192.168.123.100 not responding, still trying
[4312471.498000] nfs: server 192.168.123.100 OK
[4315229.370000] usb 4-1.4: new full speed USB device using ehci_hcd and address                           4
[4315714.420000] usb 4-1.4: USB disconnect, address 4
[4328135.860000] usb 4-1.1: new full speed USB device using ehci_hcd and address                           5
celina@tower05:~$ gphoto2 --auto-detect
Model                          Port
----------------------------------------------------------
celina@tower05:~$                                              
```
  
then, when root: 
> root@tower05:/home/celina# gphoto2 --auto-detect
Model                          Port
----------------------------------------------------------
Canon PowerShot A75            usb:
Canon PowerShot A75            usb:004,005
  
Maybe there is a way to do a : 
chmod 666 sthg ... 

:-(

---

### Post by patrick295767 on 2006-05-06
I have a kind of solution ... (working but not so great)
  
Not great but working : 
soo: 
```
sudo su
## we are as root
lsusb -t
## you check which USB device is concerned by the canon (as root)
chmod -R 666 /proc/bus/usb/004/
chmod -R uog+x  /proc/bus/usb/004/

su username
digikam
## and digikam is running as user
gphoto2 --auto-detect         # can detect the camera and as user

```
  
It works, 
but This method is not soo great ... isnt it ??
is it not okay in terms of security ??
  
And, the thing, is that, If I connect the USB camera on another USB slot, this will change ... 
So this method is not the right solution ... no ??
  
Thank you in advance ... 

Patrick

---

### Post by patrick295767 on 2006-05-06
maybe another way (for pilot) ...

```
CONFIG_USB=y
CONFIG_USB_DEBUG=y
CONFIG_USB_DEVICEFS=y
CONFIG_USB_UHCI=m
CONFIG_USB_OHCI=m
CONFIG_USB_SERIAL=m
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_VISOR=m 

&#1055;&#1086;&#1089;&#1083;&#1077; &#1101;&#1090;&#1086;&#1075;&#1086; &#1085;&#1091;&#1078;&#1085;&#1086; &#1087;&#1077;&#1088;&#1077;&#1089;&#1086;&#1073;&#1088;&#1072;&#1090;&#1100; &#1103;&#1076;&#1088;&#1086; &#1080; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;, &#1072; &#1090;&#1072;&#1082;&#1078;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1085;&#1086;&#1074;&#1086;&#1077; &#1103;&#1076;&#1088;&#1086; &#1080; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;. &#1044;&#1072;&#1083;&#1077;&#1077; &#1087;&#1077;&#1088;&#1077;&#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1077; &#1082;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;, &#1080;, &#1077;&#1089;&#1083;&#1080; &#1086;&#1087;&#1094;&#1080;&#1080; &#1090;&#1088;&#1077;&#1073;&#1091;&#1077;&#1084;&#1099;&#1077; &#1086;&#1087;&#1094;&#1080;&#1080; &#1073;&#1099;&#1083;&#1080; &#1074;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1099; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100;&#1085;&#1086;, &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1080;&#1090;&#1100; &#1084;&#1086;&#1076;&#1091;&#1083;&#1080;:

# modprobe usb-uhci 
&#1080;&#1083;&#1080;
# modprobe usb-ohci
&#1076;&#1072;&#1083;&#1077;&#1077;
# modprobe usbserial
# modprobe visor

&#1058;&#1077;&#1087;&#1077;&#1088;&#1100;, &#1074;&#1074;&#1077;&#1076;&#1103; &#1074; &#1082;&#1086;&#1085;&#1089;&#1086;&#1083;&#1080; &#1082;&#1086;&#1084;&#1072;&#1085;&#1076;&#1091; «lsmod» &#1074;&#1099; &#1076;&#1086;&#1083;&#1078;&#1085;&#1099; &#1091;&#1074;&#1080;&#1076;&#1077;&#1090;&#1100; &#1095;&#1090;&#1086;-&#1090;&#1086; &#1087;&#1086;&#1076;&#1086;&#1073;&#1085;&#1086;&#1077; &#1101;&#1090;&#1086;&#1084;&#1091;:

Module                  Size  Used by    Tainted: PF 
visor                   9036   0  (unused)
usbserial              19904   0  [visor]
usb-ohci               18080   0  (unused)
usb-uhci               23012   0  (unused)

&#1055;&#1056;&#1048;&#1052;&#1045;&#1063;&#1040;&#1053;&#1048;&#1045;!: &#1055;&#1086;&#1076;&#1088;&#1086;&#1073;&#1085;&#1077;&#1077; &#1086; &#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1080; &#1080; &#1089;&#1073;&#1086;&#1088;&#1082;&#1077; &#1103;&#1076;&#1088;&#1072; Linux &#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1079;&#1085;&#1072;&#1090;&#1100; &#1074; Linux Kernel HOWTO
(http://www.linux.org.ru/books/HOWTO/Kernel-HOWTO.html)

&#1058;&#1077;&#1087;&#1077;&#1088;&#1100; &#1087;&#1086;&#1076;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1077; &#1074;&#1072;&#1096; Palm &#1082; USB-&#1087;&#1086;&#1088;&#1090;&#1091; &#1082;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;&#1072; &#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1090;&#1080;&#1090;&#1077; HotSync. &#1042; &#1082;&#1086;&#1085;&#1089;&#1086;&#1083;&#1080; &#1080;&#1083;&#1080; &#1074; &#1083;&#1086;&#1075;&#1072;&#1093; &#1103;&#1076;&#1088;&#1072; (/var/log/messages) &#1074;&#1099; &#1076;&#1086;&#1083;&#1078;&#1085;&#1099; &#1091;&#1074;&#1080;&#1076;&#1077;&#1090;&#1100; &#1087;&#1088;&#1080;&#1084;&#1077;&#1088;&#1085;&#1086; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1077;&#1077;:

usb 1-1: new full speed USB device using address 2
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1

&#1048; &#1087;&#1086;&#1089;&#1083;&#1077; &#1090;&#1086;&#1075;&#1086; &#1082;&#1072;&#1082; Palm &#1074;&#1099;&#1076;&#1072;&#1089;&#1090;, &#1095;&#1090;&#1086; &#1089;&#1080;&#1085;&#1093;&#1088;&#1086;&#1085;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103; &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1072;&#1089;&#1100; &#1080; &#1086;&#1090;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1089;&#1103;:

usb 1-1: USB disconnect, address 4
visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
visor 1-1:1.0: device disconnected


&#1069;&#1090;&#1086; &#1079;&#1085;&#1072;&#1095;&#1080;&#1090;, &#1095;&#1090;&#1086; &#1085;&#1091;&#1078;&#1085;&#1099;&#1077; &#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;&#1072; &#1079;&#1072;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1083;&#1080; &#1080; &#1074;&#1072;&#1096; &#1050;&#1055;&#1050; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090; &#1089;&#1087;&#1077;&#1094;&#1080;&#1072;&#1083;&#1100;&#1085;&#1099;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; /dev/ttyUSB0 &#1080; /dev/ttyUSB1.

&#1058;&#1077;&#1087;&#1077;&#1088;&#1100; &#1084;&#1086;&#1078;&#1085;&#1086; &#1087;&#1077;&#1088;&#1077;&#1081;&#1090;&#1080; &#1082; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1077;&#1084;&#1091; &#1096;&#1072;&#1075;&#1091;: &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1077; &#1055;&#1054;, &#1089; &#1087;&#1086;&#1084;&#1086;&#1097;&#1100;&#1102; &#1082;&#1086;&#1090;&#1086;&#1088;&#1086;&#1075;&#1086; &#1074;&#1099; &#1089;&#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1089;&#1080;&#1085;&#1093;&#1088;&#1086;&#1085;&#1080;&#1079;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1074;&#1072;&#1096; Palm &#1089; &#1085;&#1072;&#1089;&#1090;&#1086;&#1083;&#1100;&#1085;&#1099;&#1084; &#1055;&#1050; &#1080; &#1090;.&#1076;.

&#1055;&#1054; &#1076;&#1083;&#1103; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099; &#1089; USB Palm

pilot-link (http://www.pilot-link.org) &#1080; &#1092;&#1088;&#1086;&#1085;&#1090;-&#1101;&#1085;&#1076;&#1099; &#1082; &#1085;&#1077;&#1084;&#1091;.

&#1057;&#1091;&#1097;&#1077;&#1089;&#1090;&#1074;&#1091;&#1077;&#1090; &#1085;&#1077;&#1089;&#1082;&#1086;&#1083;&#1100;&#1082;&#1086; &#1087;&#1088;&#1086;&#1077;&#1082;&#1090;&#1086;&#1074; &#1087;&#1086; &#1088;&#1072;&#1073;&#1086;&#1090;&#1077; &#1089; &#1050;&#1055;&#1050; Palm, &#1085;&#1086; &#1085;&#1072;&#1080;&#1073;&#1086;&#1083;&#1077;&#1077; &#1087;&#1086;&#1087;&#1091;&#1083;&#1103;&#1088;&#1085;&#1099;&#1084; &#1103;&#1074;&#1083;&#1103;&#1077;&#1090;&#1089;&#1103; &#1087;&#1088;&#1086;&#1077;&#1082;&#1090; pilot-link. &#1045;&#1075;&#1086; &#1084;&#1086;&#1078;&#1085;&#1086; &#1074;&#1079;&#1103;&#1090;&#1100; &#1089; &#1086;&#1092;&#1080;&#1094;&#1080;&#1072;&#1083;&#1100;&#1085;&#1086;&#1075;&#1086; &#1089;&#1072;&#1081;&#1090;&#1072; &#1080;&#1083;&#1080; &#1078;&#1077; &#1080;&#1079; &#1074;&#1072;&#1096;&#1077;&#1075;&#1086; &#1076;&#1080;&#1089;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1080;&#1074;&#1072;. &#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072; &#1089;&#1090;&#1072;&#1085;&#1076;&#1072;&#1088;&#1090;&#1085;&#1072;. &#1055;&#1086;&#1089;&#1083;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1080; &#1085;&#1091;&#1078;&#1085;&#1086; &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1077;&#1089;&#1090;&#1080; &#1085;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080;. &#1044;&#1083;&#1103; &#1085;&#1072;&#1095;&#1072;&#1083;&#1072;, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1077; &#1087;&#1088;&#1072;&#1074;&#1072; &#1095;&#1090;&#1077;&#1085;&#1080;&#1103;/&#1079;&#1072;&#1087;&#1080;&#1089;&#1080; &#1076;&#1083;&#1103; &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; /dev/ttyUSB0 &#1080; / dev/ttyUSB1, &#1090;&#1072;&#1082; &#1095;&#1090;&#1086;&#1073;&#1099; &#1080;&#1093; &#1084;&#1086;&#1078;&#1085;&#1086; &#1073;&#1099;&#1083;&#1086; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100; &#1085;&#1077; &#1090;&#1086;&#1083;&#1100;&#1082;&#1086; root'&#1091;:

# chmod 0666 /dev/ttyUSB0
# chmod 0666 /dev/ttyUSB1

&#1044;&#1072;&#1083;&#1077;&#1077; &#1074;&#1099; &#1076;&#1086;&#1083;&#1078;&#1085;&#1099; &#1091;&#1082;&#1072;&#1079;&#1072;&#1090;&#1100; &#1087;&#1086;&#1088;&#1090; &#1082; &#1082;&#1086;&#1090;&#1086;&#1088;&#1086;&#1084;&#1091; &#1073;&#1091;&#1076;&#1077;&#1090; &#1086;&#1073;&#1088;&#1072;&#1097;&#1072;&#1090;&#1100;&#1089;&#1103; pilot-link:

# export PILOTPORT=/dev/ttyUSB1


```

---

### Post by Omnios on 2006-05-06
I had a similar problem with Never WInter Nights and Gnoma2 which will only run in root. First off I took the shell script root (excuse the pun" ANyways I created a Document and typed in CD /The_Adress_Of_Device the gksudo device.
This should work.
 ```

gksudo digikam

```
 Lastly you could mod the suderers file " /etc/sudoers "

 ```

your_username ALL=NOPASSWD:digikam

```

 Hopefully this will work for you but sometimes sudo stuff is a bit finikey.

---

### Post by patrick295767 on 2006-05-07
[QUOTE=Omnios]I had a similar problem with Never WInter Nights and Gnoma2 which will only run in root. First off I took the shell script root (excuse the pun" ANyways I created a Document and typed in CD /The_Adress_Of_Device the gksudo device.
This should work.
 ```

gksudo digikam

```
 Lastly you could mod the suderers file " /etc/sudoers "

 ```

your_username ALL=NOPASSWD:digikam

```

 Hopefully this will work for you but sometimes sudo stuff is a bit finikey.[/QUOTE]
  
Thank you for you second proposed solution !
  
For the moment, I am using this one : 
```
chmod -R 666 /proc/bus/usb
chmod -R uog+x /proc/bus/usb
chmod uog-w /proc/bus/usb/devices
```
 (I placed a script in the /etc/rc2.d       and also   made use of the /etc/crontab)

---

### Post by patrick295767 on 2006-05-07
**Third method : the best  I guess !**
  
We have to change sthg in the /etc/hotplug 
(as done [here]("http://www.abul.org/article121.html") for another device (scanner))

to run the chmod script automatically ...
  
Progressing slowly ...

---

### Post by patrick295767 on 2006-05-07
the concerned file to be modified is : 
 /etc/hotplug/usb/libgphoto2

(content : 
```
#!/bin/bash

GROUP=plugdev

if [ "$ACTION" = "add" ] && [ -f "$DEVICE" ]
then
    # check if $GROUP really exists
    if getent group $GROUP > /dev/null; then
	chmod 660 "$DEVICE"
	chown root.$GROUP "$DEVICE"
    fi
fi
```
  
Would someone know next step ?

---

### Post by nekr0z on 2007-03-10
I have a PowerShot A80 and started experiencing the same problems after some system update.

---

### Post by nekr0z on 2007-03-11
I seem to have solved it. The [bug]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250") is already filed, and the solution is described there.

---

