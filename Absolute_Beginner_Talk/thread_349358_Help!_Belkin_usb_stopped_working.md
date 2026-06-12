---
title: "Help! Belkin usb stopped working"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by ITT1 on 2007-01-30
I had my Belkin wireless G adapter working fine but then one day I boott up it's not working anymore! no flashing led, no IP allocated by the router

i was using ndiswrapper and the  rt2500usb driver from the CD.

I know there's nothing wrong with the usb, since it works fine on my XP box (!)
other usb devices(HD, thumb)  I have work fine in that port

network history in System Monitor shows (or seems to show) sent and receive data which can be stopped and started by enabling/disabling the device in Networking

i've updated ndiswrapper to 1.18, and reinstalled the driver from the CD but no joy.

The thing is, I really like ubuntu and i even enjoy the little challenges like blank screen after boot.  but this sort of weirdness makes me think that i can't rely on ubuntu for any serious work. 

Is there something in one of the updates that could have caused a conflict???

Any answers? As a newbie, I'm really stuffed on this one.

---

### Post by hal10000 on 2007-01-30
You should at least post some info about the model of you adapter, also post the output of [COLOR="Red"]sudo lsusb -v[/COLOR] (if your adapter is usb).

---

### Post by ITT1 on 2007-02-02
Thanks for the reply. The belkin wireless 54g usb adapter uses FSD7050 chipset.

sudo lsusb -v gave:


Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x7050 F5D7050 ver 1000 WiFi
  bcdDevice            0.01
  iManufacturer           1 Belkin
  iProduct                2 Belkin 54g USB Network Adapter
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
      (Bus Powered)
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.17-10-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:11.2
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
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

thanks in advance for the help!

---

