---
title: "rt2x00 -How do I remove this?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by trorion on 2006-03-12
Background:
I used [this]("http://www.ubuntuforums.org/showthread.php?t=106846&highlight=2500") thread to install my USB D-Link DWL-G122 card rev.b and when I first started it up and took down my eth0 I had a killer connection to the internet.

When I restarted my system the DWL-G122 doesn't work at all.  Well, sometimes I get 100-800kbps but if I wanted that speed I would use my modem from 1995.

So how do I remove the drivers and everything?  I'm thinking I'll give them 3 months of development and then try again.

Summary of installation:
download the drivers from [SerialMonkeys]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") at /usr/src then:
```

sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
cd rt2570-1.1.0b1/Module
sudo make
sudo make install
sudo mkdir /lib/modules/`uname -r`/drivers/
sudo cp /libsudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko
sudo insmod /lib/modules/`uname -r`/drivers/rt2570.ko
sudo lsmod -a

```

edited /etc/network/interfaces to setup the card

```

sudo /etc/init.d/networking restart
sudo ifconfig rausb0 up
sudo ifconfig eth0 down

```
I unplugged eth0 (redundant since I had taken it down but meh.) and I had great connection so I:
```

sudo echo rt2570 >> /etc/modules

```
When I rebooted no internet.  Plug back in eth0 and great internet.  try restarting etc etc etc etc the usb just doesn't work.

Even tried adding ehci_hcd to my blacklist.

If no suggestions for how to fix it please let me know how to completely remove it!  Thanks in advance (learning slowly)

---

### Post by Pragmatist on 2006-03-12
What is the output of :
```
lsmod
``` 

What is the output of:
```
cat /etc/modules
```

---

### Post by trorion on 2006-03-12
[QUOTE=Pragmatist]What is the output of :
```
lsmod
``` [/QUOTE]
rt2570                155328  0

[QUOTE=Pragmatist]What is the output of:
```
cat /etc/modules
```[/QUOTE]
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
rt2570
```

---

### Post by Pragmatist on 2006-03-12
As I'm understanding it, you've gotten the device to work and you've had it work at a desirable speed.  Correct?  These are promising evidence that you can have this work the way you want it all the time.  However, especially since the instructions you followed involve alot of steps, it will take troubleshooting to figure out what is going on.  Before we get into it, is that something your willing to do?

---

### Post by Pragmatist on 2006-03-12
If you are willing to troubleshoot, try these steps out and post ALL of the results here.
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-87009e5876fdcdd0ab192c8078349cf17b254742](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-87009e5876fdcdd0ab192c8078349cf17b254742)

And, in addition to the one you posted here, have you seen this:
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)

---

### Post by trorion on 2006-03-12
[QUOTE=Pragmatist]If you are willing to troubleshoot, try these steps out and post ALL of the results here.
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-87009e5876fdcdd0ab192c8078349cf17b254742](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-87009e5876fdcdd0ab192c8078349cf17b254742)

And, in addition to the one you posted here, have you seen this:
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)[/QUOTE]
I'll give it a shot.  I suspect that's it's something to do with the auto-detect causing conflict or something.  As far as Support out of the box it didn't happen.  It recognized that there was a USB device there called D-Link DWL-122 but it didn't install anything, no lights etc.

OK, I'll re-do my /etc/network/iwconfig to start the card and post the troubleshooting.  If we figure it out then you're a genius -).  Otherwise you're a helpful smart guy.

1st my /etc/network/iwconfig file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface rausb0 inet dhcp
wireless-essid orion
wireless-mode Managed


auto eth0
auto rausb0
```

Restarting the network took about 3 minutes (sudo /etc/init.d/networking restart).  Don't see any lights on the d-link so I'm posting this then I'll edit when i know if the USB device re-started...
------------------------------------------------------
Had to re-boot to get networking again.  Took about 3 minutes on reboot for "Configuring network interfaces" stage.
---------------------------------------------------------
sudo lshw:
```
desktop
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: nVidia-nForce
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (01/28/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1833MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
---------------------------------edited out some stuff--------------------------------------------- 

        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e6081000-e6081fff irq:22
           *-usbhost
                product: nVidia Corporation nForce2 USB Controller
                vendor: Linux 2.6.12-10-386 ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@1:2
                   version: 21.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:e6086000-e6086fff irq:21
           *-usbhost
                product: nVidia Corporation nForce2 USB Controller (#2)
                vendor: Linux 2.6.12-10-386 ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e6087000-e60870ff irq:20
           *-usbhost
                product: nVidia Corporation nForce2 USB Controller
                vendor: Linux 2.6.12-10-386 ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
[B]           *-usb
                   description: Generic USB device
                   product: 802.11g WLAN Adapter
                   vendor: ANI
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=rtusb maxpower=300mA speed=480.0MB/s[/B]
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: a1
             serial: 00:e0:4c:9b:7c:1c
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.41 duplex=full ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:e6080000-e6080fff ioport:d000-d007 irq:22
---------------------------------EDITED-------------------------------------------

  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:13:46:8a:fe:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN
trorion@desktop:~$
```

---

### Post by trorion on 2006-03-12
Had to re-boot.

```
trorion@desktop:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:e0:4c:9b:7c:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.41 duplex=full ip=192.168.1.103 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:e6080000-e6080fff ioport:d000-d007 irq:22
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:13:46:8a:fe:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2500USB WLAN
trorion@desktop:~$
```

lspci:
```
trorion@desktop:~$ lspci -v | grep Ethernet
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
trorion@desktop:~$
```

lsub -v
```
trorion@desktop:~$ sudo lsusb -v

Bus 003 Device 002: ID 2001:3c00 D-Link Corp. [hex]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp. [hex]
  idProduct          0x3c00
  bcdDevice            0.01
  iManufacturer           1 ANI
  iProduct                2 802.11g WLAN Adapter
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1

Bus 003 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-10-386 ehci_hcd
  iProduct                2 nVidia Corporation nForce2 USB Controller
  iSerial                 1 0000:00:02.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xd0
  PortPwrCtrlMask    0x80
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0001.0000 C_CONNECT
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-10-386 ohci_hcd
  iProduct                2 nVidia Corporation nForce2 USB Controller (#2)
  iSerial                 1 0000:00:02.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0x81
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power

Bus 001 Device 002: ID 046d:c01d Logitech, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc01d
  bcdDevice           21.00
  iManufacturer           1 Logitech
  iProduct                2 USB-PS/2 Optical Mouse
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xa0
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      77
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0007  1x 7 bytes
        bInterval              10

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-10-386 ohci_hcd
  iProduct                2 nVidia Corporation nForce2 USB Controller
  iSerial                 1 0000:00:02.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x60
  PortPwrCtrlMask    0x90
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
trorion@desktop:~$
```

At this point I'm convinced that this driver is not installed?  Just from the short amount of knowlege I have

---

### Post by trorion on 2006-03-12
Continuing on..lsmod
```
trorion@desktop:~$ sudo lsmod
Module                  Size  Used by
rt2500                150372  0
sg                     33696  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
nvidia               4085552  12
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  4
tsdev                   7616  0
snd_mpu401              6344  1
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
ns558                   5508  0
gameport               14472  2 ns558
parport_pc             31812  1
ohci1394               30644  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm                78344  2 snd_intel8x0,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
nvsound              1541816  1
soundcore               9184  3 snd,nvsound
nvnet                  69540  0
i2c_nforce2             6528  0
i2c_core               19728  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              7964  1
agpgart                32328  2 nvidia,nvidia_agp
ntfs                   92016  1
nls_iso8859_1           4224  2
nls_cp437               5888  3
vfat                   12288  2
fat                    46492  1 vfat
dm_mod                 50364  1
evdev                   9088  0
rt2570                155328  1
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  5 rt2570,usbhid,ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  8
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  4 sg,sr_mod,sbp2,libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  533
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
trorion@desktop:~$
```

---

### Post by trorion on 2006-03-12
sudo iwconfig:
```
trorion@desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"orion"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

trorion@desktop:~$
```

---

### Post by trorion on 2006-03-12
I've decided to remove it and try again.  Maybe soon, maybe later.

Thank you for your help and encouragement though!

---

### Post by Pragmatist on 2006-03-12
Ok, but I think you have the driver or it wouldn't have the line with:  [B]RT2500USB

[/B]If you decide to work on this again, check out serialmonkey's
site again.  They have Howtos, FAQ, etc...
Also, I would try posting your problem in the other threads that
that discuss this since many of those people have first-hand
knowledge of this and will be notified when you post.

I'm still willing to help you, but, as I said before, it involve
us both spending time.

---

### Post by trorion on 2006-03-13
[QUOTE=Pragmatist]Ok, but I think you have the driver or it wouldn't have the line with:  **RT2500USB**[/QUOTE]

Hmm.  That looks wrong.  This should be using the rt2750 not the rt2500.  I just realized that.  Maybe it's being recognized as the wrong device and loading the modified PCI card drivers?  Would it make sense to blacklist it?

---

### Post by trorion on 2006-03-13
[QUOTE=trorion]Hmm.  That looks wrong.  This should be using the rt2750 not the rt2500.  I just realized that.  Maybe it's being recognized as the wrong device and loading the modified PCI card drivers?  Would it make sense to blacklist it?[/QUOTE]

Woo Hoo!  I figured out the problem then!
I did:
```
sudo ifconfig rausb0 down
sudo modprobe -r rt2570
sudo modproble -r rt2500
sudo ifconfig eth0 down
sudo modprobe rt2570
sud0 ifconfig rausb0 up
```

I'm posting this via wireless.  Now all I need to know...how to I stop my Ubuntu from installing the 2500 drivers?  I think it's a blacklist file right?

---

