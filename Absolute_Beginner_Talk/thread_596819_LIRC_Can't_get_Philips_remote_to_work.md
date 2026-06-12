---
title: "LIRC: Can't get Philips remote to work"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by DanielHB0 on 2007-10-29
I'm having trouble getting a Philips RC197 remote/ SRM 5100 to work with LISC. Unfortunately I haven't found much info on it.

[Receiver]("http://www.remotecontrol.philips.com/index.cfm?act=dspProduct&productUUID=E26615BB-C8D0-306E-2C19C86B335652AB&segmentUUID=2599F159-B824-8AE6-14B94D15FC6DDA22&id=1223")

[Remote]("http://www.remotecontrol.philips.com/index.cfm?act=dspProduct&productUUID=EBB60729-A9C1-CB8B-B0E7B3098EEABC2F&segmentUUID=2599F159-B824-8AE6-14B94D15FC6DDA22&id=1223")

It seems to be closely related to other mce remotes as it worked on XP MCE and an xbox 360 out of the box without drivers.

I'm running Ubuntu Gutsy using the latest version of LIRC (using apt)

```
Bus 001 Device 005: ID 0471:060d Philips 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0471 Philips
  idProduct          0x060d 
  bcdDevice            1.01
  iManufacturer           1  
  iProduct                2 SF+ Dongle(e.d)
  iSerial                 3 CNEA
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by rosarch on 2007-10-30
I'm having exactly the same issue with the same remote.

I followed the howto at [https://help.ubuntu.com/community/Install_Lirc_Gutsy](https://help.ubuntu.com/community/Install_Lirc_Gutsy) but no buttons are working.

:confused:

---

### Post by DanielHB0 on 2007-11-02
I couldn't get it to work and ended up making a serial receiver which works perfectly with the remote using the standard mce remote config.

---

