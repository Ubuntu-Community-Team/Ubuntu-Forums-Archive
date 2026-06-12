---
title: "Web cam, how to please"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by waltervalderrama on 2007-03-30
Please, how can i configure my micronics web cam to work with ubuntu. Do I have to recompile the kernel?? purchase another web cam brand??? If there is a tutorial or guide, please let me know. I want to chat with amsn and skype with webcam

---

### Post by chemtut on 2007-03-30
I downloaded "camorama" using synaptic and it recognised my very cheap webcam
make sure that it is plugged in at boot
good luck

---

### Post by HumanAnarchist on 2007-03-31
> **waltervalderrama said:**
> Please, how can i configure my micronics web cam to work with ubuntu. Do I have to recompile the kernel?? purchase another web cam brand??? If there is a tutorial or guide, please let me know. I want to chat with amsn and skype with webcam

Skype for linux don't support webcam :( 

Amsn do work with webcam 

Do you have more info about your webcam other than micronics? Model number? What does the command (type in terminal) "dmesg" say when you plug in your webcam? 

dmesg shows the messages that the kernel say :)

-ha-

---

### Post by ubuntu27 on 2007-04-01
> **waltervalderrama said:**
> Please, how can i configure my micronics web cam to work with ubuntu. Do I have to recompile the kernel?? purchase another web cam brand??? If there is a tutorial or guide, please let me know. I want to chat with amsn and skype with webcam

Check out the following:

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)


[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by waltervalderrama on 2007-04-01
I've tried with easycam2, but didn't get it to work. It shows me the following error. It's in french:

Aucune caméra trouvée ou caméra non compatible

---

### Post by ubuntu27 on 2007-04-02
Your webcam is not compatible.

Better buy a logitec.

Or any of the proven webcams below:

ID 054c:0154 Sony Corp.
ID 054c:0155 Sony Corp.

ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera

ID 046d:0920 Logitech, Inc. QuickCam Express
ID 0ac8:301b Z-Star Microelectronics Corp. Sansun SN-510 WebCam
ID 04fc:0561 Sunplus Technology Co., Ltd
ID 041e:4028 Creative Technology, Ltd
ID 046d:0901 Logitech, Inc. ClickSmart 510 
ID 046d:0960 Logitech, Inc. ClickSmart 420
ID 041e:4036 Creative Technology, Ltd Webcam Live
ID 041e:401e Creative Technology, Ltd WebCam NX Pro
ID 046d:0900 Logitech, Inc. ClickSmart 310
ID 0c45:60c0 Microdia
ID 041e:401d Creative Technology, Ltd WebCam NX Ultra
ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
ID 0c45:602d Microdia
ID 046d:08a2 Logitech, Inc.
ID 041e:401f Creative Technology, Ltd Webcam Notebook
ID 093a:2468 Pixart Imaging, Inc.
ID 046d:08ad Logitech, Inc.
ID 093a:2468 Pixart Imaging, Inc. CIF Single Chip
ID 041e:403a Creative Technology, Ltd WebCam NX Pro 2
ID 041e:4034 Creative Technology, Ltd

ID 046d:0850 Logitech, Inc. QuickCam Web
ID 046d:08f0 Logitech, Inc
ID 046d:08f0 Logitech, Inc.
ID 046d:0870 Logitech, Inc. QuickCam Express
ID 046d:08f5 Logitech, Inc.
ID 046d:0801 Logitech, Inc. QuickCam Home


ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
ID 0471:030c Philips PCVC690K WebCam
ID 0471:0310 Philips PCVC730K WebCam
ID 0471:0311 Philips PCVC740K ToUcam Pro

ID 05a9:8519 OmniVision Technologies, Inc.
ID 05a9:4519 OmniVision Technologies, Inc.

ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam

---

### Post by Nachowarrior on 2007-11-04
I have a logitec quick cam orbit MP any idea's on that?

---

### Post by philinux on 2007-11-04
Install Kopete from repo click configure go to devices see if it can recognise it.

---

### Post by PPPP on 2008-03-14
> **ubuntu27 said:**
> Your webcam is not compatible.

Better buy a logitec.

Or any of the proven webcams below:
...snip

**ID 046d:0801 Logitech, Inc. QuickCam Home**

...snip


I see my webcam there.  What do I need to do in order to get it to work?

I tried to install easycam but it kept failing:

```

Unpacking easycam (from .../archives/easycam_1.35_all.deb) ...
dpkg: error processing /var/cache/apt/archives/easycam_1.35_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/easycam.desktop', which is also in package easycam2
Errors were encountered while processing:
 /var/cache/apt/archives/easycam_1.35_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by HumanAnarchist on 2008-03-15
Where do you see your webcam? What list? What webcam do you have? 

From the command line post the output of:
'lsusb -v'
'lsmod -v'

I think your problem is not related to the code you posted... Looks more like your trying to replace an new version of esaycam2 with easycam1.35 dont know

I don't know anything about easycam... 

-ha-

---

### Post by PPPP on 2008-03-15
In ubuntu27's post above, he listed out some models of webcams.  I'm guessing those are the supported webcams for some driver?

I tried doing "sudo apt-get remove easycam" but it says nothing to remove...

Here's the requested info:

```
$ lsusb -v

Bus 002 Device 002: ID 0424:a700 Standard Microsystems Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0xa700 
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0089
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood      128 * 2 milli seconds
  bHubContrCurrent     49 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.22-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
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
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 006: ID 045e:002d Microsoft Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x002d 
  bcdDevice            1.00
  iManufacturer           1 Microsoft
  iProduct                2 Microsoft Internet Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          2 Microsoft Internet Keyboard
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              2 Microsoft Internet Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              2 Microsoft Internet Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc00c Optical Wheel Mouse
  bcdDevice            6.20
  iManufacturer           1 Logitech
  iProduct                2 USB Mouse
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
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
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
          wDescriptorLength      68
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.22-14-generic ohci_hcd
  iProduct                2 OHCI Host Controller
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
      bInterfaceProtocol      0 Full speed hub
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
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0303 lowspeed power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled


```


```

$ lsmod 
Module                  Size  Used by
usb_storage            73024  0 
libusual               18448  1 usb_storage
snd_rtctimer            4384  1 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
fglrx                 656352  28 
agpgart                35016  1 fglrx
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
it87                   19856  0 
hwmon_vid               4352  1 it87
i2c_isa                 5248  1 it87
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
analog                 13344  0 
gameport               16776  1 analog
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
serio_raw               8068  0 
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
pcspkr                  4224  0 
k8temp                  6656  0 
snd                    54660  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
soundcore               8800  1 snd
xpad                    9988  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_nforce2             7040  0 
i2c_core               26112  3 it87,i2c_isa,i2c_nforce2
joydev                 11328  0 
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  5 
ide_disk               18560  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ata_generic             8452  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
floppy                 60004  0 
forcedeth              51592  0 
sata_nv                20612  4 
libata                125168  2 ata_generic,sata_nv
scsi_mod              147084  4 usb_storage,sg,sd_mod,libata
ehci_hcd               36492  0 
amd74xx                15260  0 [permanent]
ide_core              116804  4 usb_storage,ide_disk,ide_cd,amd74xx
ohci_hcd               22916  0 
usbcore               138632  7 usb_storage,libusual,xpad,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  7 
apparmor               40728  0 
commoncap               8320  1 apparmor


```

---

