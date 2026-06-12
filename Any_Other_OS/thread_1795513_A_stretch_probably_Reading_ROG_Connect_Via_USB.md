---
title: "A stretch probably: Reading ROG Connect Via USB?"
date: 2011-07-02
forum: Any Other OS
---

### Post by Lucradia on 2011-07-02
Well, my Crosshair V Formula has all of its buses powered, even without the CPU (except for the PCI Slots, as evidence, the GPU isn't running.) So the ROG Connect bus is powered as well. So, I decided to flip the ROG Connect switch to the ON position and see what Linux says for the device, and what it says, is below:

```
Bus 002 Device 002: ID 1770:ff00  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1770 
  idProduct          0xff00 
  bcdDevice            1.10
  iManufacturer           1 KORYO USB
  iProduct                1 KORYO USB
  iSerial                 1 KORYO USB
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
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      57
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
Device Status:     0x000a
  (Bus Powered)
  Remote Wakeup Enabled
```

I don't know what this is, but I'm sure someone could make use of this, maybe make ROG Connect be routable to another program via USB.

---

