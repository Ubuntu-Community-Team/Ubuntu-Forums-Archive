---
title: "USB Charging"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by yanewby on 2008-01-08
Since upgrading to Gutsy my USB devices no longer charge when they are plugged in.

Under Dapper and Edgy there was no problem, simply plugging the devices in was enough to start them charging.  After upgrading to Gutsy the batteries no longer charge.  If I try to charge them in Microsoft Windows they charge perfectly (with the same cables).  This leads me to the conclusion that it is something in Gutsy that is causing the problem.

Does anyone have any ideas where to start troubleshooting this (or better how to solve the problem)?

The PC in question is a DESKTOP computer (not a laptop or notebook).  Data CAN be transferred to and from the devices by USB.

---

### Post by Mark_in_Hollywood on 2008-01-08
Post the outpout of lsusb.

Let us see whether your usb devices are listed, first.

---

### Post by philinux on 2008-01-08
Just connected my k810i and the battery displays the charging symbol on it. So that works.

---

### Post by jeffus_il on 2008-01-08
Can anyone confirm this,
The usb port has a 5volt line which is independent of the os, it should be there even when in the bios setup screens, as long as the computer is powered up ????

---

### Post by yanewby on 2008-01-09
philinux - my devices also show the battery charging symbol when they are plugged in but I can leave them plugged in all day and they will not charge.  Prior to upgrading to Gutsy my iPod used to take a few hours to fully charge from nearly flat.  Now when I plug it in it never re-charges and just seems to take enough power to stay on.  I have not changed any hardware and the only variable appears to be Gutsy.

Mark_in_Hollywood - I think my devices are listed/recognized as I can transfer data to and from them.  Here is the output of lsusb anyway:

Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 011: ID 0e79:1120  
Bus 007 Device 010: ID 05ac:1209 Apple Computer, Inc. 
Bus 007 Device 004: ID 058f:6366 Alcor Micro Corp. 
Bus 007 Device 002: ID 058f:6254 Alcor Micro Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 077d:0410 Griffin Technology PowerMate
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 045e:00db Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  

The Apple device is my iPod, the device with no identifing name is my Archos AV700.

jeffus_il - This isn't an isolated incident, if you do a quick search on the internet there are other reports of a similar nature where people cannot recharge their USB devices but nobody seems to have an answer.

It is a frustrating problem as everything used to work perfectly!

---

### Post by philinux on 2008-01-09
Ah so the phone is telling lies when it's displaying the charging symbol or it just thinks it's charging. :(

---

### Post by yanewby on 2008-01-09
Yes, the devices appear to be "telling lies" at least on my desktop PC.  

The devices (my iPod and Media Player, I do not have a phone that I charge this way) both show charging symbols when plugged in but their batteries never actually get charged.  The devices used to fully charge in a few hours flat but since upgrading to Gutsy they no longer charge.

philinux, do you have a similar problem with your phone not charging?

---

### Post by jeffus_il on 2008-01-09
Yes, I see it's a complex problem, I have had no problems on a number of gutsy machines and one hardy, with different boards and peripherals, I assumed they should work, I guess wrongly so.
Microsoft suggest connecting to a different port if there is a problem charging, and also to charge only from the back of the computer, not from a hub. They also talk about high power and low power USB ports, front panel ones can more likely be low power, a difference of 100ma to up to 500ma on the high power ones.
 They also describe ways of finding the 500ma port on the computer, and plugging your device into it.
Will do some research on Linux, maybe this is the cause of the problems?

If a USB device is connected, a
lsusb -v | less
and search for MaxPower, under you device, it will tell you the maximum power that your device can draw, I guess that it should be 500ma for a good charge.

Here is an interesting page on USB Power.
[http://www.maxim-ic.com/appnotes.cfm/an_pk/3241](http://www.maxim-ic.com/appnotes.cfm/an_pk/3241)

This extract is interesting:
>  USB Ports rarely (never) turn off power: The USB spec is not specific about this, but it is sometimes believed that USB power may be disconnected as a result of failed enumeration, or other software or firmware problems. In actual practice, no USB host shuts off USB power for anything other that an electrical fault (like a short). There may an exception to this statement, but I have yet to see it. Notebook and motherboard makers are barely willing to pay for fault protection, let alone smart power switching. So no matter what dialog takes place (or does not take place) between a USB peripheral and host, 5V (at either 500mA or 100mA, or even maybe 2A or more) will be available. This is born out by the appearance in the market of USB powered reading lights, coffee mug warmers, and other similar items that have no communication capability. They may not be "compliant," but they do function.

If a device is charging very slowly, I would suspect that it is connected to a 100ma port.

---

### Post by philinux on 2008-01-09
> **yanewby said:**
> Yes, the devices appear to be "telling lies" at least on my desktop PC.  

The devices (my iPod and Media Player, I do not have a phone that I charge this way) both show charging symbols when plugged in but their batteries never actually get charged.  The devices used to fully charge in a few hours flat but since upgrading to Gutsy they no longer charge.

philinux, do you have a similar problem with your phone not charging?


Correct. Mind you it is to a usb hub. Maybe thats it. My next pc due in late Jan will have front usb outlets, meantime I'm not routing around the back. :lolflag:

---

### Post by yanewby on 2008-01-09
I have tried a number of different USB port configurations trying to resolve this issue.

I have a PCI board with 3 extra (powered) USB ports on it - I have tried with and without this plugged in and the devices still do not charge.

My motherboard also has 4 built-in USB ports and I have tried switching my devices in each of those to see if it is a problem with one of the ports but again no success.  All of my ports are on the back of my PC.

I have also tried using a non-USB keyboard and mouse (leaving the only device attached by USB to be my iPod or Media Player) but still no charging happens.

I have tried with and without a hub... no luck.

I have not altered any hardware since I upgraded from Feisty and I know USB charging worked for me (with the same hardware) in Edgy and Feisty (and I think Dapper although some hardware may have changed since Dapper).

Any help would be appreciated and if there is anything I can do here please let me know and I can post the results as soon as possible.

---

### Post by yanewby on 2008-01-09
This is what I get for lsusb -v for my iPod:

Bus 007 Device 017: ID 05ac:1209 Apple Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05ac Apple Computer, Inc.
  idProduct          0x1209 
  bcdDevice            0.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          149
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          4 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
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
        wTotalLength           30
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          2
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               1
        iTerminal               0 
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
        bLength                35
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            9 Discrete
        tSamFreq[ 0]         8000
        tSamFreq[ 1]        11025
        tSamFreq[ 2]        12000
        tSamFreq[ 3]        16000
        tSamFreq[ 4]        22050
        tSamFreq[ 5]        24000
        tSamFreq[ 6]        32000
        tSamFreq[ 7]        44100
        tSamFreq[ 8]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               4
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.01
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     208
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
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1

For my Archos AV700:

Bus 007 Device 023: ID 0e79:1120  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0e79 
  idProduct          0x1120 
  bcdDevice            0.04
  iManufacturer          51 
  iProduct               79 
  iSerial                58 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0


The iPod has a Max Power of 500mA as you suggest but the Archos has a 0mA Max Power.  Curiously *both* are showing a charging icon - if the Archos is drawing 0mA surely it should not be charging!

When I look at all the USB port Max Power's the only ones with values greater than 0mA are the ones that have a *named* identifier (eg Apple Computer Inc or Alcor Micro Corp).  

My Archos is not named and reports 0mA (but does say it is charging on its screen!) but does not actually charge.

My Apple reports 500mA, does say it is charging on screen but does not actually charge.

---

### Post by jeffus_il on 2008-01-09
You deserve a solution after all that trying, will let you know if I find something.
Yes you have:
    MaxPower              500mA

The plot thickens:
My son has no problems charging a Creative Zen on a Gigabyte board using Gutsy Kubuntu.
My daughter charges a Sansa Express on an Asus board running Ubuntu Gutsy and has charged and ipod in the past.
I have an MSI board and am charging another Sansa  on Ubuntu  Hardy.

All are 32 bit installations.

---

