---
title: "how to safely disconnect usb devices like mp3 players"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-05-30
This may sound ridiculously simple and stupid, but I don't know how to 'safe' disconnect stuff. I can't find anything online about it either, though I didn't spend ages looking, but I would of thought it would of been easy to find. So how do I safely disconnect? It's an ipod, and when i right-click it in nautilus there is no disconnect option.

Thanks in advance.

---

### Post by aeiah on 2007-05-30
in 'computer', an icon will show up for a usb storage device. right click it and select 'eject..'

---

### Post by moredhel on 2007-05-30
Thanks, for some reason it isn't there until about 30 seconds after my ipod has been recognised, that's all xD

---

### Post by JockVSJock on 2007-08-12
***BUMP***

Will this be the same for other types of USB devices? 

For example, I have these types of USB devices: 
-Edirol USB Midi interface 
-Canon digital camera

Plugging them into the USB slot, Ubuntu automatically detects them, which is awesome, but 
unmounting them properly will cause damage.  So does a person want to go thru the Computer icon to do this? 

thanks

---

### Post by Gausian on 2007-08-12
i find that typing 

```
sudo eject /dev/nameofdevice
```

always works for me

---

### Post by wolfen69 on 2007-08-12
ive never had a problem right clicking the device icon (on the desktop) and choosing unmount.

---

### Post by mike102282 on 2007-08-12
> **wolfen69 said:**
> ive never had a problem right clicking the device icon (on the desktop) and choosing unmount.

me either that is how I do it all the time!

---

### Post by JockVSJock on 2007-08-12
I'll have to look at the desktop the next time I put a usb device in.  

BUT, right now I have a midi interface that isn't showing up on the desktop nor is it under Places > Computer 

But lsusb -v does show it: 

```

Bus 002 Device 005: ID 0582:0009 Roland Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0         8
  idVendor           0x0582 Roland Corp.
  idProduct          0x0009 
  bcdDevice            1.00
  iManufacturer           1 EDIROL
  iProduct                2 UM-1
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           79
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               70mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      0 
      iInterface              0 
      Class specific interface descriptor for class 255 is unsupported
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      0 
      iInterface              0 
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)


```

So will I have to unmount this from the command line?  

thanks

---

