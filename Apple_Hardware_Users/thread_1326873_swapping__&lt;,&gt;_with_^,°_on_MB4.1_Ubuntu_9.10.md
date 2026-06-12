---
title: "swapping  &lt;,&gt; with ^,° on MB4.1 Ubuntu 9.10"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by beauman on 2009-11-14
Does anybody know, how to [swap the keys]("https://help.ubuntu.com/community/MacBook4-1/Karmic#Swapped keys")?

---

### Post by buntuLo on 2009-11-14
oops, sorry, i asnwered you on the wrong thread..
please have a look here, most recent posts:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786")

---

### Post by beauman on 2009-11-15
The link was helpfull, especially [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786/comments/41") solved the problem for my german keyboard layout.

But how to start it automatically?

I prepared the [relevant subsection]("https://help.ubuntu.com/community/MacBook4-1/Karmic#Swapped keys") in the wiki, but it still has to be completed.

 !! OFF-TOPIC (but slightly related): 
Maybe somebody could write a subsection on how to swap the behavior of ctrl and cmd, so it equals the Mac Os behavior?
The swapped keys are quite confusing, if you are used to Mac OS, I think.

---

### Post by buntuLo on 2009-11-15
> **beauman said:**
> But how to start it automatically?
i simply created a script file as:
```
#!/bin/bash
# swapkeysonmac.sh,  correctly assign the keys §± and `~  on US-International MacbokPro5,1 keyboard
# from: https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786
#
xmodmap -e 'keycode 94=grave asciitilde grave asciitilde dead_grave dead_horn' -e 'keycode 49=section plusminus section plusminus section plusminus'
#
exit 0
```
and added it in the startup section of the kde setting panel.
the /etc/rc.local file gets executed too early, and the keyboard layout overwritten later by gnome/kde.

---

### Post by beauman on 2009-11-15
You just have to create ~/.Xmodmap and put the instructions in there. You will than be asked to use you it:

 [MacBook4.1 Wiki Ubuntu 9.10 Karmic Swapped Keys Section]("https://help.ubuntu.com/community/MacBook4-1/Karmic#Swapped keys")

Since this is settled now, I close the thread. Thanks for the link to launchpad! :p

---

### Post by beauman on 2009-11-16
Oh no! I have to reopen this thread. I just realized, that I made a mistake yesterday.

The instructions that I used in the wiki are specific to my country. buntuLo, would you mind to add your specific instructions to the wiki?

The former solution by just swapping the two keys was working for all countries, while the new solution is country-specific. Please correct me, if I am wrong!

---

### Post by buntuLo on 2009-11-16
added the link to the launchpad entry for other layouts, and copied on MBP5,1/5,2-Karmic wiki page too.
thanks for the help with ./Xmodmap !

---

### Post by _mario_ on 2009-11-16
1. there should also be a switch in GNOME's keyboard preferences to do that.
2. please do not simply circumvent the symptoms (and copy-and-paste to all pages) but also try to find the reason. since i'm running a german MBP4,1 (which has the same keyboard), i can tell that the linux kernel should really handle this problem. at least, there are quirks for that.

ciao,
Mario

---

### Post by buntuLo on 2009-11-16
> **_mario_ said:**
> there should also be a switch in GNOME's keyboard preferences to do that
ciao Mario,
there should be, indeed. at least there was, up to jaunty. i do not have that option any more since of karmic in the kde keyboard setting gui, and other users confirm that it disappeared also in gnome.
if you're aware about a better/more elegant solution in 9.10, please let us know.

---

### Post by beauman on 2009-11-17
Yes, both of you are right. _mario_, on your Jaunty install the entry should still exist: [https://help.ubuntu.com/community/MacBook4-1/Jaunty#Swapped keys]("https://help.ubuntu.com/community/MacBook4-1/Jaunty#Swapped keys"). I dislike the solution the [Karmic wiki]("https://help.ubuntu.com/community/MacBook4-1/Karmic#Swapped keys") suggests as well.

The disappearance of this option is strange. Did it vanish in both  KDE and Gnome? Was the kernel supposed to detect it right, and now it is failing again? 

Also I wonder what the background of the misdetection is anyway. Is it just a bug, so that the kernel could detect it correctly or is this problem not [observable]("http://en.wikipedia.org/wiki/Observability") at all?

I went through the [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786") one more time. There appears to be a kernel patch, but it maybe got rejected by the kernel dev team. The status of the bug is "new" (even if it was first posted one and a half year ago) and it is unassigned. Maybe the best solution would be, to call the attention of the kernel developers to this problem.

---

### Post by _mario_ on 2009-11-17
buntuLo, you're right this option did disappear in karmic. (and yes i'm running karmic, but didn't check whether it was still present.)

@beauman: i checked out the [kernel sources from git]("https://wiki.ubuntu.com/KernelTeam/KernelGitGuide") the ubuntu developers use to build their kernel packages and there's a file drivers/hid/hid-apple.c, which contains to swap those keys:
```

static const struct apple_key_translation apple_iso_keyboard[] = {
        { KEY_GRAVE,    KEY_102ND },
        { KEY_102ND,    KEY_GRAVE },
        { }
};

```

this stuff is active only if a special flag (quirk) APPLE_ISO_KEYBOARD is set for the device. this flag in turn is set for the following devices (constant and device ID):
```

USB_DEVICE_ID_APPLE_GEYSER_ISO        0x0215
USB_DEVICE_ID_APPLE_GEYSER3_ISO       0x0218
USB_DEVICE_ID_APPLE_GEYSER4_ISO       0x021b
USB_DEVICE_ID_APPLE_ALU_MINI_ISO      0x021e
USB_DEVICE_ID_APPLE_ALU_ISO           0x0221
USB_DEVICE_ID_APPLE_ALU_WIRELESS_ISO  0x022d
USB_DEVICE_ID_APPLE_WELLSPRING_ISO    0x0224
USB_DEVICE_ID_APPLE_WELLSPRING2_ISO   0x0231
USB_DEVICE_ID_APPLE_WELLSPRING3_ISO   0x0237

```

your MB4,1 should have a USB_DEVICE_ID_APPLE_WELLSPRING2_ISO (0x0231), as my MBP4,1 does.

please provide the output of:
```

lsusb | grep 05ac

```
which lists all devices made by apple (05ac is the vendor ID), as well as:
```

lsusb -v

```

ciao,
Mario

---

### Post by beauman on 2009-11-17
_mario_, good work! Very impressive! The bug seems to be basically fixed, but only for some keyboards. Did you find out further going information, like who wrote the table or why exactly these entries were chosen? 

Did you try to add your keyboard ID to the list and recompile the kernel, to prove, that this is the only place that handels with this problem?

My idea is to provide the kernel developer with a more comprehensive list.

We could generate a wiki page, where everybody who has this problem can enter his keyboard id. I wonder, if that would be feasible. It is good, that the command you suggested doesn't need superuser rights. That will scare people less. If it is just the keyboard entry we need, 
```
lsusb | grep 05ac | grep Keyboard
``` would produce less output.


If it happens for all Apple keyboards, the best thing for the kernel would be to look for the Apple vendor id and then look for the string "Keyboard". That would save the kernel from a large table. The question is of course, if it fails for *all* Apple keyboards. If not, then this solution would not work. If for the majority of Apple keyboards the keys are misdetected, the kernel could always swap the keys for an Apple keyboard, except for a list of keyboards that are known to work.

But one thing is for sure: We do need the entries in Gnome and KDE to swap the keys manually back. If it all depends on a list of dedicated keyboards, this list will most likely always be incomplete. 

Anyway, here are the outputs for a german MB 4th generation:

```

~$ lsusb | grep 05ac 
Bus 007 Device 003: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 007: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 002 Device 007: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]

~$ sudo lsusb -v
Bus 007 Device 003: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x022a Internal Keyboard/Trackpad (MacBook Pro) (ISO)
  bcdDevice            0.07
  iManufacturer           1 Apple Computer
  iProduct                2 Apple Internal Keyboard / Trackpad
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               40mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              3 Apple Internal Keyboard
      ** UNRECOGNIZED:  09 21 11 01 0d 01 22 49 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              4 Touchpad
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 59 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              3 Apple Internal Keyboard
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 14 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x8242 
  bcdDevice            0.16
  iManufacturer           1 Apple Computer, Inc.
  iProduct                2 IR Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 Apple Computer, Inc.
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 2a 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.7
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.1
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 007: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x8205 Bluetooth HCI
  bcdDevice           19.65
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          3
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
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                    1023 bytes
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1a.0
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 005 Device 005: ID 0af0:6971 Option 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0af0 Option
  idProduct          0x6971 
  bcdDevice            0.00
  iManufacturer           1 Option N.V.
  iProduct                2 Globetrotter HSDPA Modem  
  iSerial                 4 Serial Number
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           95
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
        INTERFACE CLASS:  03 24 03
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
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
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 007: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x8501 Built-in iSight [Micron]
  bcdDevice            1.84
  iManufacturer           1 Micron
  iProduct                2 Built-in iSight
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          267
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    ** UNRECOGNIZED:  08 24 00 02 ff ff ff 00
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           49
        dwClockFrequency       13.500000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                16
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  1
        bmControls           0x00000000
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x00000039
          Brightness
          Saturation
          Sharpness
          Gamma
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0 
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
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         1
        wTotalLength                      155
        bEndPointAddress                  130
        bmInfo                              0
        bTerminalLink                       3
        bStillCaptureMethod                 0
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                3
        guidFormat                            {55595659-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                383976960
        dwMaxBitRate                383976960
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             333333
        dwFrameIntervalStep                 0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                383976960
        dwMaxBitRate                383976960
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             333333
        dwFrameIntervalStep                 0
      VideoStreaming Interface Descriptor:
        bLength                            38
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                383976960
        dwMaxBitRate                383976960
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                  0
        dwMinFrameInterval             333333
        dwMaxFrameInterval             333333
        dwFrameIntervalStep                 0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass           14 Video
  bDeviceSubClass         2 Video Streaming
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
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
      bInterfaceProtocol      0 Full speed (or root) hub
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
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0503 highspeed power enable connect
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

My keyboard seems to have the id 0x022a. It is not in list. That would explain, why the swapping fails.

---

### Post by buntuLo on 2009-11-17
ciao Mario,
here's the lsusb -v output from a MacBookPro5,1.
the idProduct of the keyboard/trackpad device is 0x0237, and it is present in the list you found.
```
Bus 003 Device 003: ID 05ac:0237 Apple, Inc. 
Device Descriptor:                           
  bLength                18                  
  bDescriptorType         1                  
  bcdUSB               2.00                  
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0                             
  bDeviceProtocol         0                             
  bMaxPacketSize0         8                             
  idVendor           0x05ac Apple, Inc.                 
  idProduct          0x0237                             
  bcdDevice            0.77                             
  iManufacturer           1 Apple, Inc.                 
  iProduct                2 Apple Internal Keyboard / Trackpad
  iSerial                 0                                   
  bNumConfigurations      1
```

---

### Post by _mario_ on 2009-11-18
> **buntuLo said:**
> 
here's the lsusb -v output from a MacBookPro5,1.
the idProduct of the keyboard/trackpad device is 0x0237, and it is present in the list you found.


congrats. that means it should really work on your machine. does it?

ciao,
Mario

---

### Post by buntuLo on 2009-11-18
> **_mario_ said:**
> congrats. that means it should really work on your machine. does it?
ciao,
Mario
no Mario, that's the (sad) point: it does not work, the two keys are incorrectly mapped. it was the case in intrepid and jaunty, and i could manually correct for it with the keyboard setting option. it is still the case in karmic, and now i need to use xmodmap to assign the proper ones.

---

### Post by _mario_ on 2009-11-18
> **beauman said:**
> The bug seems to be basically fixed, but only for some keyboards. Did you find out further going information, like who wrote the table or why exactly these entries were chosen?

i assume the maintainer of the linux HID input framework. in earlier versions this stuff was hacked right into some other files. this list consists of device IDs reported by users.

> **beauman said:**
> 
Did you try to add your keyboard ID to the list and recompile the kernel, to prove, that this is the only place that handels with this problem?


no. unnecessary, because my keyboard is already present and working. i thought you have the same, but looks like i was wrong.

> **beauman said:**
> 
My idea is to provide the kernel developer with a more comprehensive list.


ideally, this list is supposed to be the most comprehensive list. but kernel hackers rely on users to report problems. they don't have all machines ever manufactured to test on. (and apple provides no documentation.) that's why i insisted at first to search the real problem and not to circumvent the symptoms.

> **beauman said:**
> 
We could generate a wiki page, where everybody who has this problem can enter his keyboard id. I wonder, if that would be feasible. It is good, that the command you suggested doesn't need superuser rights. That will scare people less. If it is just the keyboard entry we need, 
```
lsusb | grep 05ac | grep Keyboard
``` would produce less output.


a wiki page to collect this information seems be a good idea. if you do so, please also include the date the ID was added. but the command should not grep for Keyboard, because: the human-readable output on lsusb depends on a list on your machine. new devices will most likely not contain anything useful, at first. my keyboard doesn't contain the word keyboard. instead you should provide instructions how to extract the keyboard ID from `lsusb -v` or let them append the full output.

> **beauman said:**
> 
If it happens for all Apple keyboards, the best thing for the kernel would be to look for the Apple vendor id and then look for the string "Keyboard". That would save the kernel from a large table. The question is of course, if it fails for *all* Apple keyboards. If not, then this solution would not work. If for the majority of Apple keyboards the keys are misdetected, the kernel could always swap the keys for an Apple keyboard, except for a list of keyboards that are known to work.


this list (shortened by me) contains more than just keyboards, so the vendor ID isn't sufficient enough. and turning whitelisting into blacklisting isn't more useful either. instead Apple should report the right keycodes as specified by the USB HID specification.

> **beauman said:**
> 
But one thing is for sure: We do need the entries in Gnome and KDE to swap the keys manually back. If it all depends on a list of dedicated keyboards, this list will most likely always be incomplete. 


unfortunately, yes. you could try to send a patch to the Ubuntu/GNOME/KDE developers.

> **beauman said:**
> 
My keyboard seems to have the id 0x022a. It is not in list. That would explain, why the swapping fails.


actually your device is in the kernel's list. my list only contains the entries that are known to be swapped. your ID 0x022a is USB_DEVICE_ID_APPLE_GEYSER4_HF_ISO, which is not marked to be swapped. so all we have to do is add this flag. i answered to the bug report that appeared earlier in this thread. hopefully the Ubuntu developers will add this flag and send a patch upstream...

btw: instead of using xmodmap you may also add "apple:badmap" to the XKBOPTIONS variable somewhere at the end of /etc/default/console-setup. if there is already something, separate with ','. this is what the GNOME tool would do anyway.

EDIT: apple:badmap isn't present in xkb-data 1.6 (Xorg 7.4) anymore. that's why the GNOME option vanished as well.

ciao,
Mario

---

### Post by _mario_ on 2009-11-18
> **buntuLo said:**
> no Mario, that's the (sad) point: it does not work, the two keys are incorrectly mapped. it was the case in intrepid and jaunty, and i could manually correct for it with the keyboard setting option. it is still the case in karmic, and now i need to use xmodmap to assign the proper ones.

that's funny. are there any other switches active that try to swap those keys? can you please check whether the problem remains if you use the Karmic live CD.

ciao,
Mario

---

### Post by buntuLo on 2009-11-18
> **_mario_ said:**
> are there any other switches active that try to swap those keys?
no specific switches for that. i will check tonight -as i get back on my laptop- my exact keyboard configuration and post back.
> **_mario_ said:**
> can you please check whether the problem remains if you use the Karmic live CD.
almost sure that the livecd was behaving in the same way, will confirm it tonight.

---

### Post by buntuLo on 2009-11-19
> **_mario_ said:**
> are there any other switches active that try to swap those keys? can you please check whether the problem remains if you use the Karmic live CD.
Mario,
the two keys are incorrectly mapped also when running kubuntu-910-amd64 livecd.
the keyboard layout i'm using is:
```
setxkbmap -model macbook79 -layout us -variant
```
and the only three advanced options i have checked are:
```
killX=ctrl+alt+bkspc, eurosign=E, compose=rightalt
```
cia', Lo.

---

### Post by _mario_ on 2009-11-23
> **buntuLo said:**
> the two keys are incorrectly mapped also when running kubuntu-910-amd64 livecd.

did you also check the text console?
> **buntuLo said:**
> 
the keyboard layout i'm using is:
```
setxkbmap -model macbook79 -layout us -variant
```
and the only three advanced options i have checked are:
```
killX=ctrl+alt+bkspc, eurosign=E, compose=rightalt
```

those options shouldn't be important, but which layout did you select? i tried different defined layouts, but none seemed to work:
```

#setxkbmap -model macbook79 -layout us
#setxkbmap -model macbook79 -layout us -variant basic
Error loading new keyboard description
#setxkbmap -model macbook79 -layout us -variant intl
Error loading new keyboard description

```
using -model pc105 instead, does work. all 3 variants result in the same keys: left of 1 is `. right of left shift is <. would this be correct?

ciao,
Mario

---

### Post by buntuLo on 2009-11-23
> **_mario_ said:**
> did you also check the text console?
yes, same behaviour on tty1 and on tty7_Xorg, running from HD or liveCD.
> **_mario_ said:**
> 
buntuLo: the keyboard layout i'm using is:
         setxkbmap -model macbook79 -layout us -variant
those options shouldn't be important, but which layout did you select? 
as i wrote, US layout. i also tried all possible variants with it.
> **_mario_ said:**
> i tried different defined layouts, but none seemed to work:
```

#setxkbmap -model macbook79 -layout us
#setxkbmap -model macbook79 -layout us -variant basic
Error loading new keyboard description
#setxkbmap -model macbook79 -layout us -variant intl
Error loading new keyboard description

```
using -model pc105 instead, does work.

-model pc105 or -model macbook79 doesn't make any difference for me.
> **_mario_ said:**
> all 3 variants result in the same keys: left of 1 is `. right of left shift is <. would this be correct?
and here's the problem: this is not correct. i attach a picture of my keyboard, sold in the Netherlands as Dutch/International English. sorry for the bad quality, but you should be able to see that left of 1 is §/±, right of left shift is `/~.
thanks for looking into it.

---

### Post by _mario_ on 2009-11-24
> **buntuLo said:**
> yes, same behaviour on tty1 and on tty7_Xorg, running from HD or liveCD.

that means the kernel might be reporting the wrong keycodes.
> **buntuLo said:**
> 
and here's the problem: this is not correct. i attach a picture of my keyboard, sold in the Netherlands as Dutch/International English. sorry for the bad quality, but you should be able to see that left of 1 is §/±, right of left shift is `/~.
i see. but that means those keys are not only swapped, but also mapped to the wrong symbols, as i got '<' instead of '§/±'.

this is going to be difficult. if you're interested we should:
[LIST=1]
[*] check whether the kernel reports the correct keycodes.
[*] find out how a standard (PC-style) international english layout should look like.
[*] the differences of Apple's international english layout.
[*] fix whatever is wrong.
[/LIST]

ciao,
Mario

---

### Post by buntuLo on 2009-11-24
> **_mario_ said:**
> i see. but that means those keys are not only swapped, but also mapped to the wrong symbols, as i got '<' instead of '§/±'.
correct. one is swapped, the other one mapped to </>, keys which are already present on top of ,/< and ./> .
> **_mario_ said:**
> this is going to be difficult. if you're interested we should:
[LIST=1]
[*] check whether the kernel reports the correct keycodes.
[*] find out how a standard (PC-style) international english layout should look like.
[*] the differences of Apple's international english layout.
[*] fix whatever is wrong.
[/LIST]
i am not interested for myself (as xmodmap is an easy workaround), but i'm definitely interested in helping out for a better compatibility of ubuntu on this hardware, even though i have not much time to spend on it. i'd appreciate if you could guide me through the necessary test steps.
would it be worth opening a new thread with a more meaningful title, in order to collect informations from more people about the keyboard layouts that are around (point #3 in your list)?

---

### Post by _mario_ on 2009-11-30
> **buntuLo said:**
> 
i am not interested for myself (as xmodmap is an easy workaround), but i'm definitely interested in helping out for a better compatibility of ubuntu on this hardware, even though i have not much time to spend on it. 


i agree. i've been sick the last week. and now i've a lot of work to do at the university. maybe it's better to just wait and in the meantime fix using xmodmap.

ciao,
Mario

---

