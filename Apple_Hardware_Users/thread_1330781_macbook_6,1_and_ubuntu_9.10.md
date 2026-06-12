---
title: "macbook 6,1 and ubuntu 9.10"
date: 2009-11-18
forum: Apple Hardware Users
---

### Post by zypcu on 2009-11-18
did anyone install the karmic on the new macbook? what daes work and what doesn't? thanks

---

### Post by kstan_79 on 2009-11-19
Working:
Display card (Proprietary driver)
USB
Touchpad
Webcam
battery sensor
Sound (Recompile latest alsa source code fix the problem)

Not-working
================

Wifi (Initially working, but don't know after what update cause it fail again, I can't settle it at all)


Others
=========
Cannot restart computer (Shutdown work properly.)

---

### Post by _mario_ on 2009-11-19
since you seem to be the first user, can you please post the ouput of:
```

# sudo dmidecode --string system-product-name
# lspci -n
# lspci -v
# lsusb -v

```
some developers might be interested in this information.

thanks & ciao,
Mario

---

### Post by jcupitt on 2009-12-03
9.10 x64 on a 6,1 macbook. Sound output doesn't work, nv-185 didn't work, nv-173 seems fine.

EDIT --- nv-185 is now working for me, I guess an update fixed it

```

$ sudo dmidecode --string system-product-name
MacBook6,1
$ lspci -n
00:00.0 0600: 10de:0a82 (rev b1)
00:00.1 0500: 10de:0a88 (rev b1)
00:03.0 0601: 10de:0aae (rev b3)
00:03.1 0500: 10de:0aa4 (rev b1)
00:03.2 0c05: 10de:0aa2 (rev b1)
00:03.3 0500: 10de:0a89 (rev b1)
00:03.4 0500: 10de:0a98 (rev b1)
00:03.5 0b40: 10de:0aa3 (rev b1)
00:04.0 0c03: 10de:0aa5 (rev b1)
00:04.1 0c03: 10de:0aa6 (rev b1)
00:06.0 0c03: 10de:0aa7 (rev b1)
00:06.1 0c03: 10de:0aa9 (rev b1)
00:08.0 0403: 10de:0ac0 (rev b1)
00:09.0 0604: 10de:0aab (rev b1)
00:0a.0 0200: 10de:0ab0 (rev b1)
00:0b.0 0101: 10de:0ab5 (rev b1)
00:10.0 0604: 10de:0aa0 (rev b1)
00:15.0 0604: 10de:0ac6 (rev b1)
02:00.0 0300: 10de:0863 (rev b1)
03:00.0 0280: 14e4:4353 (rev 01)
$ lspci -v
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2000 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel, IRQ 15
	I/O ports at 2180 [size=64]
	I/O ports at 2140 [size=64]
	I/O ports at 2100 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 14
	Memory at 93300000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at 93388000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at 93389200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at 93387000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at 93389100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at 93380000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 93200000-932fffff
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
	Memory at 93386000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 21e0 [size=8]
	Memory at 93389000 (32-bit, non-prefetchable) [size=256]
	Memory at 93389300 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 25
	I/O ports at 21d8 [size=8]
	I/O ports at 21ec [size=4]
	I/O ports at 21d0 [size=8]
	I/O ports at 21e8 [size=4]
	I/O ports at 21c0 [size=16]
	Memory at 93384000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 92000000-930fffff
	Prefetchable memory behind bridge: 0000000080000000-0000000091ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 93100000-931fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M] (rev b1)
	Subsystem: Apple Computer Inc. Device 00bd
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 92000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 1000 [size=128]
	[virtual] Expansion ROM at 93000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
	Subsystem: Apple Computer Inc. Device 0093
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at 93100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl
$ sudo lsusb -v
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x8507 
  bcdDevice            4.30
  iManufacturer           1 Apple Inc.
  iProduct                2 Built-in iSight
  iSerial                 3 8T9A9J60HAKQ3A00
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          642
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               2 Built-in iSight
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              2 Built-in iSight
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           51
        dwClockFrequency        4.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x0000000a
          Auto-Exposure Mode
          Exposure Time (Absolute)
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
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
        wTotalLength                      423
        bEndPointAddress                  130
        bmInfo                              0
        bTerminalLink                       2
        bStillCaptureMethod                 2
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                5
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  5
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 1 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            70
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                 11
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            363636
        dwFrameInterval( 2)            400000
        dwFrameInterval( 3)            444444
        dwFrameInterval( 4)            500000
        dwFrameInterval( 5)            571428
        dwFrameInterval( 6)            666667
        dwFrameInterval( 7)            800000
        dwFrameInterval( 8)           1000000
        dwFrameInterval( 9)           1333333
        dwFrameInterval(10)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            70
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         333333
        bFrameIntervalType                 11
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            363636
        dwFrameInterval( 2)            400000
        dwFrameInterval( 3)            444444
        dwFrameInterval( 4)            500000
        dwFrameInterval( 5)            571428
        dwFrameInterval( 6)            666667
        dwFrameInterval( 7)            800000
        dwFrameInterval( 8)           1000000
        dwFrameInterval( 9)           1333333
        dwFrameInterval(10)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            70
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         333333
        bFrameIntervalType                 11
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            363636
        dwFrameInterval( 2)            400000
        dwFrameInterval( 3)            444444
        dwFrameInterval( 4)            500000
        dwFrameInterval( 5)            571428
        dwFrameInterval( 6)            666667
        dwFrameInterval( 7)            800000
        dwFrameInterval( 8)           1000000
        dwFrameInterval( 9)           1333333
        dwFrameInterval(10)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            70
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         333333
        bFrameIntervalType                 11
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            363636
        dwFrameInterval( 2)            400000
        dwFrameInterval( 3)            444444
        dwFrameInterval( 4)            500000
        dwFrameInterval( 5)            571428
        dwFrameInterval( 6)            666667
        dwFrameInterval( 7)            800000
        dwFrameInterval( 8)           1000000
        dwFrameInterval( 9)           1333333
        dwFrameInterval(10)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            70
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                 24576000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         333333
        bFrameIntervalType                 11
        dwFrameInterval( 0)            333333
        dwFrameInterval( 1)            363636
        dwFrameInterval( 2)            400000
        dwFrameInterval( 3)            444444
        dwFrameInterval( 4)            500000
        dwFrameInterval( 5)            571428
        dwFrameInterval( 6)            666667
        dwFrameInterval( 7)            800000
        dwFrameInterval( 8)           1000000
        dwFrameInterval( 9)           1333333
        dwFrameInterval(10)           2000000
      VideoStreaming Interface Descriptor:
        bLength                            26
        bDescriptorType                    36
        bDescriptorSubtype                  3 (STILL_IMAGE_FRAME)
        bEndpointAddress                    0
        bNumImageSizePatterns               5
        wWidth( 0)                        160
        wHeight( 0)                       120
        wWidth( 1)                        176
        wHeight( 1)                       144
        wWidth( 2)                        320
        wHeight( 2)                       240
        wWidth( 3)                        352
        wHeight( 3)                       288
        wWidth( 4)                        640
        wHeight( 4)                       480
        bNumCompressionPatterns             5
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 1 (BT.709)
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
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
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
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
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
        wMaxPacketSize     0x0b00  2x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
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
        wMaxPacketSize     0x0c00  2x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       6
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
        wMaxPacketSize     0x1380  3x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       7
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

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
  iManufacturer           3 Linux 2.6.31-15-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:04.1
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
  nNbrPorts             7
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
   Port 7: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 002: ID 05ac:0237 Apple, Inc. 
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
  bcdDevice            0.81
  iManufacturer           1 Apple Inc.
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
      ** UNRECOGNIZED:  09 21 11 01 0d 01 22 9c 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              4 Touchpad
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 1b 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              4 Touchpad
      ** UNRECOGNIZED:  09 21 11 01 00 01 22 34 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)

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
  iManufacturer           3 Linux 2.6.31-15-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:04.0
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
  nNbrPorts             7
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0103 power enable connect
   Port 7: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.31-15-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:06.1
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
  nNbrPorts             5
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
   Port 5: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 005: ID 05ac:8218 Apple, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x8218 
  bcdDevice            0.15
  iManufacturer           1 Broadcom Corp
  iProduct                2 Bluetooth Module
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
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
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
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
        wTransferSize                      64 bytes
Device Status:     0x0001
  Self Powered

Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0         8
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x4500 
  bcdDevice            1.00
  iManufacturer           1 Apple Inc.
  iProduct                2 BRCM2070 Hub
  iSerial                 0 
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
    MaxPower               94mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x0e
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
Device Status:     0x0001
  Self Powered

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
  iManufacturer           3 Linux 2.6.31-15-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:06.0
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
  nNbrPorts             5
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```

---

### Post by isaaccp on 2009-12-24
I have one of those too. the nvidia 185 works here. shutdown doesn't work properly, it gets stuck in the end, after printing:
Restarting system.

Sound doesn't work either yet for me.

Cheers!

---

### Post by jcupitt on 2009-12-29
> **isaaccp said:**
> 

Sound doesn't work either yet for me.



Nor me. I spent some time trying to get it working: it seems you need to download and build the latest ALSA. I had a go but I guess I messed up somewhere because it didn't work (for me).

I suppose 10.04 will work.

---

### Post by kstan_79 on 2009-12-29
recompile the source code, alsa working. But this time I'm facing problem for wireless cannot connect (ubuntu or kubuntu). This problem occur since when I dunno. Now I'm been force to use cable or MacOS to surf net.

---

### Post by aprigiosimoes on 2010-01-01
for shutdown and reboot in macbook 6,1

add in /etc/default/grub IN default OR in /boot/grub/grub.cfg --> reboot=pci

  .... splash quiet reboot=pci


bye;

---

### Post by rah on 2010-01-04
I also have a MacBook 6,1 and there's no sound in Ubuntu.  I've seen a few references to recompiling ALSA.  Which code are we talking about?  The driver?  The firmware?

EDIT

I've installed the latest ALSA snapshot using the ALSA Upgrade Script available here:

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

but my computer is still mute.  I'll post again when I've got it fixed.

/EDIT

---

### Post by rah on 2010-01-10
BUMP

Has anyone besides kstan_79 managed to get sound working yet?

---

### Post by kstan_79 on 2010-01-11
So far I'd recompile the source code, initialy I can't listen any sound until I change the volume level at alsamixer command (Ubuntu GUI is not working well).

---

### Post by rah on 2010-01-16
I've got sound!!

I tried updating ALSA with soundcheck's script as I described before.  I also disabled pulseaudio as described in this post:

[http://ubuntuforums.org/showpost.php...15&postcount=2](http://ubuntuforums.org/showpost.php...15&postcount=2)

(I still have pulseaudio disabled and I'm not sure if that's necessary, but anyway....)

Nothing was working, so I tried OSS4 -- ossxmix is a great little mixer! -- but that was mute too.

So I uninstalled OSS4 and used soundcheck's script to install the latest ALSA again.  Same problem:  when I do ```
aplay -l
```no devices are recognised, and when I do ```
alsamixer
```it claims that "This sound device does not have any controls".  Hmmm.

Then I found this site:

[http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html](http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html)

which suggested this as a fix:

```
sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
```

and it's working!!  Yay!!

Music!  Videos!  Video games!  :D

Thanks to everyone who helped me out!

---

### Post by isaaccp on 2010-01-16
I posted that sound wasn't working to me and it started to work for me just a few minutes later.

Just installed the ALSA backport and added the model=mbp5 bit to this line in /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel power_save=10 power_save_controller=N model=mbp5

Cheers!

---

### Post by alexmurray on 2010-01-17
Can someone post the contents of /proc/asound/card0/codec#0 and I'll write a patch to make sure this works automatically in future versions of alsa.

---

### Post by jcupitt on 2010-01-17
> **alexmurray said:**
> Can someone post the contents of /proc/asound/card0/codec#0 and I'll write a patch to make sure this works automatically in future versions of alsa.

Here you go:

```

$ cat /proc/asound/card0/codec#0
Codec: Cirrus Logic CS4206
Address: 0
Function Id: 0x1
Vendor Id: 0x10134206
Subsystem Id: 0x106b0100
Revision Id: 0x100301
No Modem Function Group found
Default PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=0, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=1, dir=1, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0x6e 0x6e]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x03 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0xd7 0xd7]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x04 [Audio Output] wcaps 0xd041d: Stereo Amp-Out
  Amp-Out caps: ofs=0x73, nsteps=0x7f, stepsize=0x01, mute=1
  Amp-Out vals:  [0xd5 0xd5]
  Converter: stream=0, channel=0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x05 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0xb3 0xb3] [0xb3 0xb3]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0c* 0x12
Node 0x06 [Audio Input] wcaps 0x18051b: Stereo Amp-In
  Amp-In caps: ofs=0x33, nsteps=0x3f, stepsize=0x03, mute=1
  Amp-In vals:  [0x3f 0x3f] [0x3f 0x3f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1f5]: 8000 16000 32000 44100 48000 88200 96000
    bits [0x1e]: 16 20 24 32
    formats [0x3]: PCM FLOAT
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 2
     0x0d* 0x0e
Node 0x07 [Audio Input] wcaps 0x180791: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Preemphasis Copyright
  Digital category: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 8 samples
  Connection: 1
     0x0f
Node 0x08 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x09 [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x012b4030: [Jack] HP Out at Ext Rear
    Conn = Comb, Color = Green
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x02
Node 0x0a [Pin Complex] wcaps 0x410581: Stereo
  Pincap 0x00000054: OUT Detect Balanced
  Pin Default 0x90100121: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
  Connection: 1
     0x03
Node 0x0b [Pin Complex] wcaps 0x410101: Stereo
  Pincap 0x00000050: OUT Balanced
  Pin Default 0x90100120: [Fixed] Speaker at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Delay: 1 samples
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000024: IN Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0d [Pin Complex] wcaps 0x41048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001764: IN Detect Balanced
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x90a00110: [Fixed] Mic at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x0e [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x0f [Pin Complex] wcaps 0x410681: Stereo Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Delay: 1 samples
Node 0x10 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014be040: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x08
Node 0x11 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=22
Node 0x12 [Pin Complex] wcaps 0x41000b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
Node 0x13 [Beep Generator Widget] wcaps 0x700000: Mono
Node 0x14 [Audio Output] wcaps 0x40611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x7]: PCM FLOAT AC3
  Power: setting=D0, actual=D0
  Delay: 4 samples
Node 0x15 [Pin Complex] wcaps 0x410301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x400000f0: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Delay: 1 samples
  Connection: 1
     0x14

```

---

### Post by jcupitt on 2010-01-19
> **isaaccp said:**
> 
Just installed the ALSA backport and added the model=mbp5 bit to this line in /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel power_save=10 power_save_controller=N model=mbp5


Still not working here :( 

Here's what I've done:

[LIST]
[*]fresh install of 9.10
[*]sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
[*]added model=mbp5 to /etc/modprobe.d/alsa-base.conf, as noted above ^^
[*]turn up the volume (it's on zero on boot)
[/LIST]

I've not tried disabling pulseaudio, would that help? I tried alsamixer too, but still nothing.

---

### Post by linuxopjemac on 2010-01-19
> I tried alsamixer too, but still nothing. Did you unmute all channels ?

---

### Post by jcupitt on 2010-01-20
> **linuxopjemac said:**
> Did you unmute all channels ?

That did it! I was changing the channel volumes, but I hadn't spotted the separate mute on each channel.

So: select front speaker, press 'm', turn up the volume, it works. Thank you very much everyone.

---

### Post by linuxopjemac on 2010-01-20
Congratulations!

Feel free to write us a nice report how to install Ubuntu on a new MacBook 6,1 and what you did to get everything working ;)

---

### Post by jcupitt on 2010-01-21
I have one more discovery: my sound was very weak and tinny, far worse than previous laptops.

I was messing about in alsamixer and found that if I switched to the Capture screen with TAB and then increased the surround volume there, suddenly everything sounded great. Why does increasing the capture volume help playback? No idea.

Summary: start alsamixer, use cursor left/right to move between channels, for each channel use cursor up to put the volume at max, press 'm' to unmute every channel, press TAB to flip between screens. Make sure everything is unmuted and at max.

---

### Post by jcupitt on 2010-01-21
Here's a summary post of what I had to do to get Ubuntu 9.10 working on a MacBook 6,1. Not my work of course, just summarising the thread.

[LIST]

[*]Install 64-bit Ubuntu 9.10

[*]Ubuntu will fail to reboot, it stops at "restarting system". To fix this: 

```
sudo vi /etc/default/grub
```

and change the line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to be:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
```

Now do:

```
sudo update-grub
```

[*]Sound will not work. The chipset is supported by the latest ALSA (Linux sound system), but not by the one that ships with 9.10. To fix this, enter:

```
sudo apt-get install linux-backports-modules-alsa-2.6.31-17-generic
```

This will install a more recent ALSA for you. Enter:

```
sudo vi /etc/modprobe.d/alsa-base.conf
```

and change the line:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

to be:

```
options snd-hda-intel power_save=10 power_save_controller=N model=mbp5
```

[*]Now reboot. It'll still freeze at the "Restarting system" step, just hold down the power button for a few seconds. Next time you reboot it should work.

[*]Start alsamixer and make sure every channel on every page is set to maximum and is not muted. Press 'm' to toggle mute, press cursor up/down to change volume, press cursor left/right to change channels, press Tab to change pages.

[/LIST]

Currently my one remaining issue is the thing taking a long time to come out of suspend, 23s according to /var/log/messages. Does anyone else have this problem?

---

### Post by linuxopjemac on 2010-01-21
Thanks a lot. It found a place too on my website :)

[http://mac.linux.be/content/karmic-koala-macbook-61](http://mac.linux.be/content/karmic-koala-macbook-61)

---

### Post by isaaccp on 2010-01-25
> **jcupitt said:**
> Currently my one remaining issue is the thing taking a long time to come out of suspend, 23s according to /var/log/messages. Does anyone else have this problem?

Yeah, same here. Old Macbook used to come back to life in 2 seconds, this one takes ages. The sound is working for me, but sometimes it won't work at all (videos get stuck because not being able to reproduce sound or something).

---

### Post by jcupitt on 2010-01-26
Here's what appears in /var/log/messages during suspend / resume. Some mysterious text also flashes on the screen just before the login prompt appears, I don't know if it's the same as this.

I'm not sure this is very helpful though. Where else should I look for diagnostics?

```

Jan 26 09:15:36 banana kernel: [32092.029489] PM: Syncing filesystems ... done.
Jan 26 09:15:36 banana kernel: [32092.032837] Freezing user space processes ... (elapsed 1.87 seconds) done.
Jan 26 09:15:36 banana kernel: [32093.910222] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jan 26 09:15:36 banana kernel: [32093.910263] Suspending console(s) (use no_console_suspend to debug)
Jan 26 09:15:36 banana kernel: [32093.970107] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan 26 09:15:36 banana kernel: [32093.970224] sd 0:0:0:0: [sda] Stopping disk
Jan 26 09:15:36 banana kernel: [32094.480332] wl 0000:03:00.0: PCI INT A disabled
Jan 26 09:15:36 banana kernel: [32094.500212] wl 0000:03:00.0: power state changed by ACPI to D3
Jan 26 09:15:36 banana kernel: [32094.560410] forcedeth 0000:00:0a.0: wake-up capability disabled by ACPI
Jan 26 09:15:36 banana kernel: [32094.560415] forcedeth 0000:00:0a.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32094.710114] HDA Intel 0000:00:08.0: PCI INT A disabled
Jan 26 09:15:36 banana kernel: [32094.730096] ehci_hcd 0000:00:06.1: PCI INT B disabled
Jan 26 09:15:36 banana kernel: [32094.730102] ohci_hcd 0000:00:06.0: PCI INT A disabled
Jan 26 09:15:36 banana kernel: [32094.730108] ehci_hcd 0000:00:04.1: PCI INT B disabled
Jan 26 09:15:36 banana kernel: [32094.730114] ohci_hcd 0000:00:04.0: PCI INT A disabled
Jan 26 09:15:36 banana kernel: [32094.730171] PM: suspend devices took 0.820 seconds
Jan 26 09:15:36 banana kernel: [32094.730404] ehci_hcd 0000:00:06.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32094.750032] ohci_hcd 0000:00:06.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32094.770035] ehci_hcd 0000:00:04.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32094.790031] ohci_hcd 0000:00:04.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32095.030067] ACPI: Preparing to enter system sleep state S3
Jan 26 09:15:36 banana kernel: [32095.150193] Disabling non-boot CPUs ...
Jan 26 09:15:36 banana kernel: [32095.260016] CPU 1 is now offline
Jan 26 09:15:36 banana kernel: [32095.260018] SMP alternatives: switching to UP code
Jan 26 09:15:36 banana kernel: [32095.265888] CPU1 is down
Jan 26 09:15:36 banana kernel: [32095.265960] Extended CMOS year: 2000
Jan 26 09:15:36 banana kernel: [32095.265960] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 26 09:15:36 banana kernel: [32095.265960] Extended CMOS year: 2000
Jan 26 09:15:36 banana kernel: [32095.265960] Enabling non-boot CPUs ...
Jan 26 09:15:36 banana kernel: [32095.265960] SMP alternatives: switching to SMP code
Jan 26 09:15:36 banana kernel: [32095.274449] Booting processor 1 APIC 0x1 ip 0x6000
Jan 26 09:15:36 banana kernel: [32095.265578] Initializing CPU#1
Jan 26 09:15:36 banana kernel: [32095.265578] Calibrating delay using timer specific routine.. 4510.72 BogoMIPS (lpj=22553604)
Jan 26 09:15:36 banana kernel: [32095.265578] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 26 09:15:36 banana kernel: [32095.265578] CPU: L2 cache: 3072K
Jan 26 09:15:36 banana kernel: [32095.265578] CPU 1/0x1 -> Node 0
Jan 26 09:15:36 banana kernel: [32095.265578] CPU: Physical Processor ID: 0
Jan 26 09:15:36 banana kernel: [32095.265578] CPU: Processor Core ID: 1
Jan 26 09:15:36 banana kernel: [32095.265578] mce: CPU supports 6 MCE banks
Jan 26 09:15:36 banana kernel: [32095.265578] CPU1: Thermal monitoring enabled (TM2)
Jan 26 09:15:36 banana kernel: [32095.265578] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Jan 26 09:15:36 banana kernel: [32095.431460] CPU1: Intel(R) Core(TM)2 Duo CPU     P7550  @ 2.26GHz stepping 0a
Jan 26 09:15:36 banana kernel: [32095.472514] CPU1 is up
Jan 26 09:15:36 banana kernel: [32095.472517] ACPI: Waking up from system sleep state S3
Jan 26 09:15:36 banana kernel: [32096.310423] ohci_hcd 0000:00:04.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32096.310462] ehci_hcd 0000:00:04.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32096.310488] ohci_hcd 0000:00:06.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32096.310526] ehci_hcd 0000:00:06.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.610293] nForce2_smbus 0000:00:03.2: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.610299] ohci_hcd 0000:00:04.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.610306] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 19 (level, low) -> IRQ 19
Jan 26 09:15:36 banana kernel: [32114.640091] ehci_hcd 0000:00:04.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.640097] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 21 (level, low) -> IRQ 21
Jan 26 09:15:36 banana kernel: [32114.640110] ohci_hcd 0000:00:06.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.640115] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 18 (level, low) -> IRQ 18
Jan 26 09:15:36 banana kernel: [32114.670095] ehci_hcd 0000:00:06.1: PME# disabled
Jan 26 09:15:36 banana kernel: [32114.670101] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 20 (level, low) -> IRQ 20
Jan 26 09:15:36 banana kernel: [32114.670115] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
Jan 26 09:15:36 banana kernel: [32114.670147] forcedeth 0000:00:0a.0: wake-up capability disabled by ACPI
Jan 26 09:15:36 banana kernel: [32114.670152] forcedeth 0000:00:0a.0: PME# disabled
Jan 26 09:15:36 banana kernel: [32115.302537] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 26 09:15:36 banana kernel: [32115.302553] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 26 09:15:36 banana kernel: [32115.304342] ata1.00: configured for UDMA/133
Jan 26 09:15:36 banana kernel: [32115.307605] ata2.00: configured for UDMA/100
Jan 26 09:15:36 banana kernel: [32115.324319] ata1.00: configured for UDMA/133
Jan 26 09:15:36 banana kernel: [32115.324321] ata1: EH complete
Jan 26 09:15:36 banana kernel: [32115.327618] ata2.00: configured for UDMA/100
Jan 26 09:15:36 banana kernel: [32115.327620] ata2: EH complete
Jan 26 09:15:36 banana kernel: [32119.251373] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
Jan 26 09:15:36 banana kernel: [32119.683310] sd 0:0:0:0: [sda] Starting disk
Jan 26 09:15:36 banana kernel: [32120.227625] PM: resume devices took 23.910 seconds
Jan 26 09:15:36 banana kernel: [32120.227626] ------------[ cut here ]------------
Jan 26 09:15:36 banana kernel: [32120.227634] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:53 suspend_test_finish+0x82/0x90()
Jan 26 09:15:36 banana kernel: [32120.227636] Hardware name: MacBook6,1
Jan 26 09:15:36 banana kernel: [32120.227637] Component: resume devices, time: 23910
Jan 26 09:15:36 banana kernel: [32120.227638] Modules linked in: nls_utf8 hfsplus usb_storage snd_hda_codec_cirrus binfmt_misc ppdev bridge stp snd_hda_intel bnep snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd lib80211_crypt_tkip soundcore nvidia(P) snd_page_alloc uvcvideo videodev wl(P) i2c_nforce2 v4l1_compat shpchp v4l2_compat_ioctl32 lib80211 bcm5974 btusb iptable_filter lp parport ip_tables x_tables joydev applesmc led_class input_polldev hid_apple usbhid forcedeth
Jan 26 09:15:36 banana kernel: [32120.227669] Pid: 8679, comm: pm-suspend Tainted: P        W  2.6.31-17-generic #54-Ubuntu
Jan 26 09:15:36 banana kernel: [32120.227671] Call Trace:
Jan 26 09:15:36 banana kernel: [32120.227676]  [<ffffffff8105e7d8>] warn_slowpath_common+0x78/0xb0
Jan 26 09:15:36 banana kernel: [32120.227679]  [<ffffffff8105e86c>] warn_slowpath_fmt+0x3c/0x40
Jan 26 09:15:36 banana kernel: [32120.227682]  [<ffffffff810935c2>] suspend_test_finish+0x82/0x90
Jan 26 09:15:36 banana kernel: [32120.227685]  [<ffffffff81093369>] suspend_devices_and_enter+0xa9/0xe0
Jan 26 09:15:36 banana kernel: [32120.227688]  [<ffffffff81093478>] enter_state+0xd8/0x110
Jan 26 09:15:36 banana kernel: [32120.227690]  [<ffffffff81092a32>] state_store+0x92/0x100
Jan 26 09:15:36 banana kernel: [32120.227695]  [<ffffffff812747c7>] kobj_attr_store+0x17/0x20
Jan 26 09:15:36 banana kernel: [32120.227698]  [<ffffffff81184dc0>] sysfs_write_file+0xe0/0x160
Jan 26 09:15:36 banana kernel: [32120.227702]  [<ffffffff8111f3b8>] vfs_write+0xb8/0x1a0
Jan 26 09:15:36 banana kernel: [32120.227706]  [<ffffffff8152c7b4>] ? do_page_fault+0x194/0x370
Jan 26 09:15:36 banana kernel: [32120.227709]  [<ffffffff8111fe6c>] sys_write+0x4c/0x80
Jan 26 09:15:36 banana kernel: [32120.227713]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Jan 26 09:15:36 banana kernel: [32120.227715] ---[ end trace fc2e5a007a80c01a ]---
Jan 26 09:15:36 banana kernel: [32120.228079] Restarting tasks ... done.
Jan 26 09:15:36 banana kernel: [32120.332848] eth0: no link during initialization.
Jan 26 09:15:36 banana kernel: [32120.333332] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by yngd on 2010-01-28
Installed "lucid" daily Jan27, on my Macbook6,1
Worked perfectly with sound, wifi.

If anybody doesn't like Karmic, lucid will be your friend.:popcorn:

---

### Post by jcupitt on 2010-01-28
> **yngd said:**
> Installed "lucid" daily Jan27, on my Macbook6,1
Worked perfectly with sound, wifi.

That's interesting. Do you have fast suspend / resume as well (ie. less than 20 seconds)?

---

### Post by yngd on 2010-01-29
Suspend doesn't work.. either in Karmic as you know.

Today I found GLX not working. (nvidia driver 195 works without GLX at least)

ALSA --> you don't need any CLI work. just go alsamixser -> Unmute.

---

### Post by IndieRockSteve on 2010-02-19
how do you set up the keyboard and mouse to behave "like they do in OSX"?

i'd like to remap the ctrl/alt keys to behave like they do in OSX.

Also, the touchpad doesn't seem to work with multiple finger touches, so if I want to click and drag it won't work. how can I fix this?

thanks!

---

### Post by jcupitt on 2010-03-12
> **IndieRockSteve said:**
> i'd like to remap the ctrl/alt keys to behave like they do in OSX.

Mine is set to MacBook (intl) UK in Prefs / KB and alt/ctrl seem to work. I do have a very minor issue: the +-para key (very top left) generates `~, and the ~` key (bottom left) generates ><. 

> **IndieRockSteve said:**
> Also, the touchpad doesn't seem to work with multiple finger touches, so if I want to click and drag it won't work. how can I fix this?

I can do two-finger scrolling, is that what you mean? OS X's fancy multitouch stuff is not supported as far as I know.

---

### Post by IndieRockSteve on 2010-04-04
> **jcupitt said:**
> I can do two-finger scrolling, is that what you mean? OS X's fancy multitouch stuff is not supported as far as I know.

well on mine, it doesn't seem to like the fact that there is no separate button, and so when i try to click it moves the cursor, rather annoying.

---

