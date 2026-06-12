---
title: "Wi Fi Internet Connection"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Mikey Daniels on 2007-12-29
I have installed 7.10 on an AMD 64 Athlon computer on a second hard drive. Previously had 6.10 and 7.04 on the drive and they connected to Wi Fi broadband connection fine.

When I put mouse over connection icon at top of screen get "No Network Connection" message. If Right Click get "Enable Networking" which is ticked.

Go to System - Admnistration - Network and only see Wired Connection and Modem Connection options.

I cannot connect using ethernet as router is too far away.

I see that there have been many issues re connection with 7.10 but I haven't found anything on the forums yet which gives a novice like me some guide to the first part of this issue.

Does anyone have any help they can offer?

Thanks

Mike

---

### Post by ugm6hr on 2007-12-29
First thought:
In **System->Administration->Network**, do you wave a wireless connection listed?  If so - select it, and click Properties and try with "Roaming" enabled.
Then try again.

If that doesn't help - post the output from:
```
lspci
lshw -C network
```
You are looking for the wifi relevant entries.

---

### Post by Mikey Daniels on 2007-12-29
Thanks. No, there is no wireless connection listed. How do I check the code?

---

### Post by ugm6hr on 2007-12-29
> **Mikey Daniels said:**
> Thanks. No, there is no wireless connection listed. How do I check the code?

See the link below regarding Terminal.

---

### Post by famleon on 2007-12-29
Hi, I am triying to set up my wifi conection and it is not working, I have a compaq presario C500 (C568LA), original with Windows Vista (sorry for the foul language..) I removed the OS and installed Ubunto 7.10 everything seems to be working really smooth, with the exception of the wifi, in windows you must push a button to activate the wifi, but here the button is disable. and everytime that I try to connect sometimes connect, but no IP address assigned or working, any Idea? I mean the idea of the wifi is to work from anywhere and I do not want to carry my cable arround the house....200 mts cable...and to be honest I love the speed and everyting related to UBUNTU, great OS, also I know this is not the topic, but where I can look for drivers for new devices (TV capture cards, etc...) and why the button is not working and does not light on or is disable...sorry i need to get rid of my windows mind and start thinking LINUX...

---

### Post by CJ56 on 2007-12-29
If you're happy that the drivers are downloaded and installed for your wi-fi card, have you installed wi-fi radar? It's in the repositories (make sure multiverse etc. are enabled) and when you've installed it, comes up in the Internet section of the Applications menu.

On my old Inspiron it found all the local networks; I picked the one I wanted, went through the drop-down menus (choosing Auto whenever I could) and it did the rest.

---

### Post by famleon on 2007-12-29
Now is working...and i have WiFi. I used the restrited drivers and now is working

---

### Post by Mikey Daniels on 2007-12-30
Hi ugm6hr, The output is as follows:

mike@mike-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
00:0a.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
mike@mike-desktop:~$ 

mike@mike-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
00:0a.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
mike@mike-desktop:~$ 

Hope it means someting to you, it doesn't to me.

---

### Post by ugm6hr on 2007-12-30
```

00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

This is the only Network controller - and I am sure it is a wired ethernet card (since it is the same one in my laptop).

What hardware are you using?  And is there an "on" light for your wifi?  If so - it seems likely that you need a hardware switch to turn your wifi on.  Is it built-in, or PCI/USB/PCMCIA?

---

### Post by Mikey Daniels on 2007-12-30
I've got a BT Home Hub Router connected to the PC by a wireless connector.

The Ubuntu OS is on a second hard drive I have had installed to the PC. Prior to 7.10 installation the connection was working fine with 7.04 and 6.10. The wireles connection works fine wth MS on the original hard drive.

Regarding an on light for the WiFi, all lights on the router are on and connection is fine on the laptop I am writing this on.

I don't know what you mean by "it seems likely that you need a hardware switch to turn your wifi on. Is it built-in, or PCI/USB/PCMCIA?"

Mike

---

### Post by ugm6hr on 2007-12-30
So it is a desktop computer.  Is the wifi card in the computer a USB card, or a PCI card?

I am not sure why it is not even recognised by lspci if it is PCI.  The only thing I have heard of is that Windows sometimes software turns off ethernet cards when you log out, and Ubuntu can't turn it back on.

How did you get it to work in 7.04?

---

### Post by Mikey Daniels on 2007-12-30
I presume the WiFi card in the PC is PCI (whatever that is) as I haven't had to do anything to the PC to enable WiFi other than follow the instructions from BT to set up the Home Hub. No cards have had to be fitted to the PC and the connection is via a receiver which fits into a USB port in the back of the PC. Or is this what you mean by a USB Card?

I didn't have to do anything to make Ubuntu work in 7.04 other than install it. It was only after installing 7.10 that the WiFi connection refused to work.

---

### Post by ugm6hr on 2007-12-30
> **Mikey Daniels said:**
> No cards have had to be fitted to the PC and the connection is via a receiver which fits into a USB port in the back of the PC. Or is this what you mean by a USB Card?

I didn't have to do anything to make Ubuntu work in 7.04 other than install it. It was only after installing 7.10 that the WiFi connection refused to work.

So it is a USB card...

I have never used a USB wifi card, but it is worth starting with the outputs of the following commands:
```
lsusb -v
lshw -C network
ifconfig
```

---

### Post by Mikey Daniels on 2007-12-30
> **ugm6hr said:**
> So it is a USB card...

I have never used a USB wifi card, but it is worth starting with the outputs of the following commands:
```
lsusb -v
lshw -C network
ifconfig
```

Here goes:

lsusb -v

bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
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
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 0000:0000  
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
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 0000:0000  
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
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
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
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 0000:0000  
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
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0040 Wheel Mouse Optical
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                3 
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
          wDescriptorLength      72
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
cannot read device status, Operation not permitted (1)

Bus 001 Device 004: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0556 Asahi Kasei Microsystems Co., Ltd
  idProduct          0x0001 AK5370 I/F A/D Converter
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          118
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           38
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          2
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               3
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 8
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x03
          Mute
          Volume
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           2
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                23
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            5 Discrete
        tSamFreq[ 0]         8000
        tSamFreq[ 1]        11025
        tSamFreq[ 2]        22050
        tSamFreq[ 3]        44100
        tSamFreq[ 4]        48000
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0064  1x 100 bytes
        bInterval               1
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
cannot read device status, Operation not permitted (1)

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
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

mike@mike-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:0f:ea:39:96:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
mike@mike-desktop:~$ 

mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:39:96:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by ugm6hr on 2007-12-30
OK.  That shows that the wifi card is not recognized as a network controller (ifconfig and lshw -C network show only wired ethernet).

I am assuming that this must be the wifi card (since the other USB device is a mouse):
```
Bus 001 Device 004: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
```

Maybe try lsusb with the wifi device unplugged to make sure that this disappears.

I'm afraid a bit of searching about this might be required...

EDIT: I think this is actually a microphone or sound device.... So your wifi card is not even recognised as being inserted.  Hmmmm...

---

### Post by Mikey Daniels on 2007-12-31
> **ugm6hr said:**
> OK.  That shows that the wifi card is not recognized as a network controller (ifconfig and lshw -C network show only wired ethernet).

I am assuming that this must be the wifi card (since the other USB device is a mouse):
```
Bus 001 Device 004: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
```

Maybe try lsusb with the wifi device unplugged to make sure that this disappears.

I'm afraid a bit of searching about this might be required...

EDIT: I think this is actually a microphone or sound device.... So your wifi card is not even recognised as being inserted.  Hmmmm...

Any advice gratefuly received!

---

### Post by ugm6hr on 2007-12-31
I'm afraid I'm out of ideas, assuming you ran the above commands with the device plugged in.

Perhaps someone else can help?

---

### Post by Mikey Daniels on 2007-12-31
> **ugm6hr said:**
> I'm afraid I'm out of ideas, assuming you ran the above commands with the device plugged in.

Perhaps someone else can help?

Thanks for your time anyway. The item is a microphone so I haven't run the command you sent over.

Let's see if anyone else has any ideas?

---

### Post by Mikey Daniels on 2007-12-31
> **Mikey Daniels said:**
> Thanks for your time anyway. The item is a microphone so I haven't run the command you sent over.

Let's see if anyone else has any ideas?

The WiFi Adapter plugged into USB port is a BT Voyager 1055 and specifies that it's compatible with Windows 2000 and XP. Looking at the forums it may be that I need the drivers for this specific USB connection. Does anyonenknow where I can get these from?

Thanks

---

### Post by RelativelyQuantum on 2007-12-31
You might want to try madwifi; that's a driver that was recommended to me to get wifi working on my macbook. No guarantee it will work with your hardware, but it might be worth a try. Here's the code:

```
sudo aptitude install build-essential

wget http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz

tar -zxvf madwifi<tab>

cd madwifi<tab>

make

sudo make install
```

Enter these into terminal one at a time. That'll install madwifi; again, its just a shot.

Hope this helps.

---

### Post by gigaferz on 2007-12-31
hello!
 why dont you open a terminal window, and type  "dmesg" , then unplug the adapter and then plug it again, and type "dmesg" again, the last lines will show you some activity.

And will give you information about your device

I looked around and looks like the way to get it working is with ndiswrapper

---

### Post by Mikey Daniels on 2008-01-01
> **RelativelyQuantum said:**
> You might want to try madwifi; that's a driver that was recommended to me to get wifi working on my macbook. No guarantee it will work with your hardware, but it might be worth a try. Here's the code:

```
sudo aptitude install build-essential

wget http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz

tar -zxvf madwifi<tab>

cd madwifi<tab>

make

sudo make install
```

Enter these into terminal one at a time. That'll install madwifi; again, its just a shot.

Hope this helps.

Thanks for the message. Here's the output when I try.

mike@mike-desktop:~$ sudo aptitude install build-essential
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
  linux-libc-dev patch 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7416kB of archives. After unpacking 31.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)' in the drive '/cdrom/' and press [Enter].

Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main dpkg-dev 1.14.5ubuntu16
  File not found
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88046 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu9_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch/patch_2.5.9-4_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu9) ...
Setting up patch (2.5.9-4) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

E: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb: File not found
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
mike@mike-desktop:~$ wget [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
--13:05:16--  [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
           => `madwifi-trunk-current.tar.gz'
Resolving snapshots.madwifi.org... failed: Name or service not known.
mike@mike-desktop:~$ tar -zxvf madwifi<tab>
bash: syntax error near unexpected token `newline'
mike@mike-desktop:~$ cd madwifi<tab>
bash: syntax error near unexpected token `newline'
mike@mike-desktop:~$ make
make: *** No targets specified and no makefile found. Stop.
mike@mike-desktop:~$ sudo make install
make: *** No rule to make target `install'. Stop.
mike@mike-desktop:~$

---

### Post by Mikey Daniels on 2008-01-01
> **gigaferz said:**
> hello!
 why dont you open a terminal window, and type  "dmesg" , then unplug the adapter and then plug it again, and type "dmesg" again, the last lines will show you some activity.

And will give you information about your device

I looked around and looks like the way to get it working is with ndiswrapper

Here's the output from dmesg. Does it help?

[   44.675259] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   44.675299] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[   44.675301] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   44.675304] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   46.124526] eth0: link down
[   46.210322] ppdev: user-space parallel port driver
[   46.515863] audit(1199192392.792:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4844 profile="/usr/sbin/cupsd"
[   46.783779] Failure registering capabilities with primary security module.
[   46.958185] Bluetooth: Core ver 2.11
[   46.958289] NET: Registered protocol family 31
[   46.958292] Bluetooth: HCI device and connection manager initialized
[   46.958295] Bluetooth: HCI socket layer initialized
[   46.976496] Bluetooth: L2CAP ver 2.8
[   46.976502] Bluetooth: L2CAP socket layer initialized
[   47.060105] Bluetooth: RFCOMM socket layer initialized
[   47.060191] Bluetooth: RFCOMM TTY layer initialized
[   47.060194] Bluetooth: RFCOMM ver 1.8
[   47.373060] Marking TSC unstable due to cpufreq changes
[   47.373787] Time: acpi_pm clocksource has been installed.
[  149.786111] UDF-fs: No VRS found
[  149.809057] ISO 9660 Extensions: Microsoft Joliet Level 3
[  149.837976] ISO 9660 Extensions: RRIP_1991A
[  178.030503] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[  178.030509] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[  178.030512] ide: failed opcode was: unknown
[  179.959443] hdc: error code: 0x70  sense_key: 0x03  asc: 0x02  ascq: 0x00
[  179.959449] end_request: I/O error, dev hdc, sector 524
[  179.959649] ISOFS: unable to read i-node block
[  260.622506] usb 5-3: new high speed USB device using ehci_hcd and address 5
[  260.734658] usb 5-3: configuration #1 chosen from 1 choice
[  260.780692] usbcore: registered new interface driver libusual
[  260.811126] Initializing USB Mass Storage driver...
[  260.811240] scsi2 : SCSI emulation for USB Mass Storage devices
[  260.811347] usb-storage: device found at 5
[  260.811350] usb-storage: waiting for device to settle before scanning
[  260.811475] usbcore: registered new interface driver usb-storage
[  260.811544] USB Mass Storage support registered.
[  263.316005] usb-storage: device scan complete
[  263.316377] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[  263.341367] sd 2:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  263.341865] sd 2:0:0:0: [sda] Write Protect is off
[  263.341869] sd 2:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  263.341871] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  263.346178] sd 2:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  263.346615] sd 2:0:0:0: [sda] Write Protect is off
[  263.346618] sd 2:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  263.346620] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  263.346623]  sda: sda1
[  263.347860] sd 2:0:0:0: [sda] Attached SCSI removable disk
[  263.358751] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  304.364336] usb 5-3: USB disconnect, address 5
mike@mike-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=58e71881-b759-49c0-849d-009802dd0198 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 131056) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6720 checksum 0
[    0.000000] ACPI: RSDP 000F6720, 0014 (r0 VIAK8 )
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 1FFF30C0, 4898 (r1 VIAK8  AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7980, 005A (r1 VIAK8  AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 131056) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   131056
[    0.000000] On node 0 totalpages: 130959
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2819 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1735 pages used for memmap
[    0.000000]   DMA32 zone: 125225 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 128044
[    0.000000] Kernel command line: root=UUID=58e71881-b759-49c0-849d-009802dd0198 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[   25.303333] time.c: Detected 1999.969 MHz processor.
[   25.304547] Console: colour VGA+ 80x25
[   25.304563] Checking aperture...
[   25.304566] CPU 0: aperture @ e8000000 size 64 MB
[   25.311517] Memory: 504332k/524224k available (2274k kernel code, 19504k reserved, 1181k data, 296k init)
[   25.311572] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.389335] Calibrating delay using timer specific routine.. 4003.75 BogoMIPS (lpj=8007512)
[   25.389375] Security Framework v1.0.0 initialized
[   25.389387] SELinux:  Disabled at boot.
[   25.389447] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   25.389973] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   25.390225] Mount-cache hash table entries: 256
[   25.390381] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.390384] CPU: L2 Cache: 512K (64 bytes/line)
[   25.390386] CPU 0/0 -> Node 0
[   25.390408] SMP alternatives: switching to UP code
[   25.390620] Freeing SMP alternatives: 24k freed
[   25.391190] Early unpacking initramfs... done
[   25.708407] ACPI: Core revision 20070126
[   25.708467] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.752209] Using local APIC timer interrupts.
[   25.802215] result 12499804
[   25.802217] Detected 12.499 MHz APIC timer.
[   25.805380] Brought up 1 CPUs
[   25.805729] NET: Registered protocol family 16
[   25.805806] ACPI: bus type pci registered
[   25.805813] PCI: Using configuration type 1
[   25.806589] ACPI: EC: Look up EC in DSDT
[   25.810773] ACPI: Interpreter enabled
[   25.810780] ACPI: (supports S0 S1 S4 S5)
[   25.810803] ACPI: Using IOAPIC for interrupt routing
[   25.815612] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.815619] PCI: Probing PCI hardware (bus 00)
[   25.816482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.853176] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   25.853304] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[   25.853439] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[   25.853551] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.853659] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.853763] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.853867] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.853971] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   25.854120] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[   25.854269] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[   25.854438] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[   25.854587] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[   25.854661] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.854676] pnp: PnP ACPI init
[   25.854683] ACPI: bus type pnp registered
[   25.857754] pnp: PnP ACPI: found 14 devices
[   25.857756] ACPI: ACPI bus type pnp unregistered
[   25.857819] PCI: Using ACPI for IRQ routing
[   25.857822] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.857832] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   25.857957] NET: Registered protocol family 8
[   25.857959] NET: Registered protocol family 20
[   25.858012] agpgart: Detected AGP bridge 0
[   25.860222] agpgart: AGP aperture is 64M @ 0xe8000000
[   25.860301] pnp: 00:00: iomem range 0xd0000-0xd7fff has been reserved
[   25.860304] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   25.860307] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   25.860310] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   25.860316] pnp: 00:02: ioport range 0x4000-0x407f has been reserved
[   25.860319] pnp: 00:02: ioport range 0x40f0-0x40ff has been reserved
[   25.860325] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   25.860578] PCI: Bridge: 0000:00:01.0
[   25.860580]   IO window: disabled.
[   25.860584]   MEM window: ec000000-edffffff
[   25.860588]   PREFETCH window: e0000000-e7ffffff
[   25.860601] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.860639] NET: Registered protocol family 2
[   25.861344] Time: tsc clocksource has been installed.
[   25.893384] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   25.893450] TCP established hash table entries: 16384 (order: 6, 393216 bytes)
[   25.893709] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   25.893951] TCP: Hash tables configured (established 16384 bind 16384)
[   25.893954] TCP reno registered
[   25.905475] checking if image is initramfs... it is
[   26.517624] Freeing initrd memory: 7735k freed
[   26.525083] audit: initializing netlink socket (disabled)
[   26.525097] audit(1199192372.172:1): initialized
[   26.526893] VFS: Disk quotas dquot_6.5.1
[   26.526943] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   26.527043] io scheduler noop registered
[   26.527045] io scheduler anticipatory registered
[   26.527047] io scheduler deadline registered
[   26.527131] io scheduler cfq registered (default)
[   26.527145] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.527648] Boot video device is 0000:01:00.0
[   26.549440] Real Time Clock Driver v1.12ac
[   26.549525] Linux agpgart interface v0.102 (c) Dave Jones
[   26.549528] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.549626] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.549768] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.550226] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.550436] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.550588] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.550826] 0000:00:0a.0: ttyS2 at I/O 0x9008 (irq = 18) is a 16450
[   26.550979] 0000:00:0a.0: ttyS3 at I/O 0x9010 (irq = 18) is a 8250
[   26.551053] Couldn't register serial port 0000:00:0a.0: -28
[   26.551562] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.551759] input: Macintosh mouse button emulation as /class/input/input0
[   26.551826] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.551828] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.552220] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.552224] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.552367] mice: PS/2 mouse device common for all mice
[   26.552563] TCP cubic registered
[   26.552626] NET: Registered protocol family 1
[   26.552833] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   26.552841] Freeing unused kernel memory: 296k freed
[   26.621415] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.727985] AppArmor: AppArmor initialized<5>audit(1199192373.376:2):  type=1505 info="AppArmor initialized" pid=1212
[   27.734818] fuse init (API version 7.8)
[   27.738988] Failure registering capabilities with primary security module.
[   28.309686] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.369270] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ee000000-ee0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   28.416473] SCSI subsystem initialized
[   28.421373] libata version 2.21 loaded.
[   28.422643] sata_via 0000:00:0f.0: version 2.2
[   28.422943] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[   28.422946] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   28.422954] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[   28.423007] sata_via 0000:00:0f.0: routed to hard irq line 11
[   28.423120] scsi0 : sata_via
[   28.423163] scsi1 : sata_via
[   28.423188] ata1: SATA max UDMA/133 cmd 0x0000000000019400 ctl 0x0000000000019802 bmdma 0x000000000001a400 irq 20
[   28.423192] ata2: SATA max UDMA/133 cmd 0x0000000000019c00 ctl 0x000000000001a002 bmdma 0x000000000001a408 irq 20
[   28.476185] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.493644] usbcore: registered new interface driver usbfs
[   28.493670] usbcore: registered new interface driver hub
[   28.493694] usbcore: registered new device driver usb
[   28.494484] USB Universal Host Controller Interface driver v3.0
[   28.574239] Floppy drive(s): fd0 is 1.44M
[   28.618043] FDC 0 is a post-1991 82077
[   28.629315] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   28.849297] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   28.864524] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.864531] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.866964] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   28.866989] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[   28.867002] VP_IDE: chipset revision 6
[   28.867004] VP_IDE: not 100% native mode: will probe irqs later
[   28.867014] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   28.867023]     ide0: BM-DMA at 0xac00-0xac07, BIOS settings: hda:DMA, hdb:DMA
[   28.867035]     ide1: BM-DMA at 0xac08-0xac0f, BIOS settings: hdc:DMA, hdd:DMA
[   28.867043] Probing IDE interface ide0...
[   29.289376] hda: ExcelStor Technology J880, ATA DISK drive
[   29.573370] hdb: MAXTOR STM3802110A, ATA DISK drive
[   29.629926] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.640676] Probing IDE interface ide1...
[   29.669356] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00004c0100004081]
[   30.513354] hdc: ASUS CRW-5232AS, ATAPI CD/DVD-ROM drive
[   31.297338] hdd: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
[   31.353617] ide1 at 0x170-0x177,0x376 on irq 15
[   31.354748] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   31.354753] 8139cp 0000:00:13.0: Try the "8139too" driver instead.
[   31.356872] 8139too Fast Ethernet driver 0.9.28
[   31.357284] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   31.358091] eth0: RealTek RTL8139 at 0xffffc200000e8000, 00:0f:ea:39:96:48, IRQ 18
[   31.358096] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   31.358458] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   31.358461] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   31.358468] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   31.358479] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   31.358746] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   31.358777] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b000
[   31.359152] usb usb1: configuration #1 chosen from 1 choice
[   31.359290] hub 1-0:1.0: USB hub found
[   31.359297] hub 1-0:1.0: 2 ports detected
[   31.365699] hda: max request size: 512KiB
[   31.377889] hda: Host Protected Area detected.
[   31.377892]  current capacity is 160834367 sectors (82347 MB)
[   31.377893]  native  capacity is 160836480 sectors (82348 MB)
[   31.378268] hda: Host Protected Area disabled.
[   31.378271] hda: 160836480 sectors (82348 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(133)
[   31.378421] hda: cache flushes supported
[   31.378467]  hda: hda1
[   31.392301] hdb: max request size: 512KiB
[   31.439079] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   31.463421] hdb: cache flushes supported
[   31.463450]  hdb:<6>ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   31.465383] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   31.465403] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   31.465425] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b400
[   31.465524] usb usb2: configuration #1 chosen from 1 choice
[   31.465547] hub 2-0:1.0: USB hub found
[   31.465555] hub 2-0:1.0: 2 ports detected
[   31.486891]  hdb1 hdb2 < hdb5 >
[   31.529662] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   31.529671] Uniform CD-ROM driver Revision: 3.20
[   31.531069] hdd: ATAPI 40X DVD-ROM drive, 1725kB Cache, UDMA(33)
[   31.573401] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   31.573416] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   31.573440] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   31.573463] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800
[   31.573593] usb usb3: configuration #1 chosen from 1 choice
[   31.573618] hub 3-0:1.0: USB hub found
[   31.573626] hub 3-0:1.0: 2 ports detected
[   31.681366] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   31.681380] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   31.681402] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   31.681424] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000bc00
[   31.681520] usb usb4: configuration #1 chosen from 1 choice
[   31.681548] hub 4-0:1.0: USB hub found
[   31.681555] hub 4-0:1.0: 2 ports detected
[   31.705251] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   31.789481] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[   31.789683] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   31.789739] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   31.789786] ehci_hcd 0000:00:10.4: irq 21, io mem 0xee002000
[   31.825300] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.825444] usb usb5: configuration #1 chosen from 1 choice
[   31.825469] hub 5-0:1.0: USB hub found
[   31.825479] hub 5-0:1.0: 8 ports detected
[   32.239694] Attempting manual resume
[   32.239698] swsusp: Resume From Partition 3:69
[   32.239700] PM: Checking swsusp image.
[   32.239865] PM: Resume from disk failed.
[   32.241270] usb 1-1: device not accepting address 2, error -71
[   32.268856] kjournald starting.  Commit interval 5 seconds
[   32.268867] EXT3-fs: mounted filesystem with ordered data mode.
[   33.857206] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   33.995956] usb 5-7: configuration #1 chosen from 1 choice
[   34.237203] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   34.432915] usb 1-1: configuration #1 chosen from 1 choice
[   34.677189] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   34.866945] usb 1-2: configuration #1 chosen from 1 choice
[   40.073402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.154531] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.880305] input: PC Speaker as /class/input/input2
[   40.996255] parport_pc 00:0b: reported by Plug and Play ACPI
[   40.996303] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.394126] usbcore: registered new interface driver hiddev
[   41.420224] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input3
[   41.420603] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-2
[   41.420620] usbcore: registered new interface driver usbhid
[   41.420623] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.447292] usbcore: registered new interface driver cdc_ether
[   41.449801] usb 5-7: bad CDC descriptors
[   41.449824] usbcore: registered new interface driver rndis_host
[   41.722584] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   41.722589] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   41.722598] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[   41.722739] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.767110] usbcore: registered new interface driver snd-usb-audio
[   42.830114] lp0: using parport0 (interrupt-driven).
[   42.909553] Adding 1494004k swap on /dev/hdb5.  Priority:-1 extents:1 across:1494004k
[   43.296847] EXT3 FS on hdb1, internal journal
[   44.256989] No dock devices found.
[   44.352089] input: Power Button (FF) as /class/input/input4
[   44.356359] ACPI: Power Button (FF) [PWRF]
[   44.384296] input: Power Button (CM) as /class/input/input5
[   44.388523] ACPI: Power Button (CM) [PWRB]
[   44.675259] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   44.675299] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[   44.675301] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   44.675304] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   46.124526] eth0: link down
[   46.210322] ppdev: user-space parallel port driver
[   46.515863] audit(1199192392.792:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4844 profile="/usr/sbin/cupsd"
[   46.783779] Failure registering capabilities with primary security module.
[   46.958185] Bluetooth: Core ver 2.11
[   46.958289] NET: Registered protocol family 31
[   46.958292] Bluetooth: HCI device and connection manager initialized
[   46.958295] Bluetooth: HCI socket layer initialized
[   46.976496] Bluetooth: L2CAP ver 2.8
[   46.976502] Bluetooth: L2CAP socket layer initialized
[   47.060105] Bluetooth: RFCOMM socket layer initialized
[   47.060191] Bluetooth: RFCOMM TTY layer initialized
[   47.060194] Bluetooth: RFCOMM ver 1.8
[   47.373060] Marking TSC unstable due to cpufreq changes
[   47.373787] Time: acpi_pm clocksource has been installed.
[  149.786111] UDF-fs: No VRS found
[  149.809057] ISO 9660 Extensions: Microsoft Joliet Level 3
[  149.837976] ISO 9660 Extensions: RRIP_1991A
[  178.030503] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[  178.030509] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[  178.030512] ide: failed opcode was: unknown
[  179.959443] hdc: error code: 0x70  sense_key: 0x03  asc: 0x02  ascq: 0x00
[  179.959449] end_request: I/O error, dev hdc, sector 524
[  179.959649] ISOFS: unable to read i-node block
[  260.622506] usb 5-3: new high speed USB device using ehci_hcd and address 5
[  260.734658] usb 5-3: configuration #1 chosen from 1 choice
[  260.780692] usbcore: registered new interface driver libusual
[  260.811126] Initializing USB Mass Storage driver...
[  260.811240] scsi2 : SCSI emulation for USB Mass Storage devices
[  260.811347] usb-storage: device found at 5
[  260.811350] usb-storage: waiting for device to settle before scanning
[  260.811475] usbcore: registered new interface driver usb-storage
[  260.811544] USB Mass Storage support registered.
[  263.316005] usb-storage: device scan complete
[  263.316377] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.00 PQ: 0 ANSI: 2
[  263.341367] sd 2:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  263.341865] sd 2:0:0:0: [sda] Write Protect is off
[  263.341869] sd 2:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  263.341871] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  263.346178] sd 2:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  263.346615] sd 2:0:0:0: [sda] Write Protect is off
[  263.346618] sd 2:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  263.346620] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  263.346623]  sda: sda1
[  263.347860] sd 2:0:0:0: [sda] Attached SCSI removable disk
[  263.358751] sd 2:0:0:0: Attached scsi generic sg0 type 0
[  304.364336] usb 5-3: USB disconnect, address 5
[  383.267326] usb 5-7: USB disconnect, address 4
[  394.693319] usb 5-7: new high speed USB device using ehci_hcd and address 6
[  394.760730] usb 5-7: configuration #1 chosen from 1 choice
[  394.760808] usb 5-7: bad CDC descriptors
mike@mike-desktop:~$

---

