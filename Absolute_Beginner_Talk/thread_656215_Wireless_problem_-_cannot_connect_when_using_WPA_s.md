---
title: "Wireless problem - cannot connect when using WPA security"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by majabl on 2008-01-02
I've recently decided to have a go with Ubuntu 7.10 on my main computer (not the one in my sig), but don't want to install the OS until I can get wireless networking going.  So at the moment I'm running from the CD version.

Everything is working fine except for the wireless networking.  I have a USB wireless card and when booting that computer under Windows XP everything works perfectly.

When I boot into Ubuntu the card appears to be working and seeing my router: when I click on the network icon up by the clock I can see an option with my router's SSID.  When I choose that option I am presented with a box asking for the WPA Personal key, which I have input correctly (yes, I've checked! ;)).  Then the network icon changes as it tries to connect, but after a while it gives up and returns to the original box asking for the WPA Personal key.  There are no error messages.

I've turned off security on my router and Ubuntu can then connect to it without any problems - I see green lights on the changed network icon, and then some bars indicating the strength of the connection, and I'm able to navigate the web and access the internet in other ways.  But leaving a router without security isn't an ideal long-term option....

My router is set to:
[LIST]
[*]broadcast network name
[*]allow new devices automatically
[*]use WPA-PSK as the security mode, and WPA as the WPA-PSK version
[*]use TKIP WPA-PSK encryption (I've tried setting this in Ubuntu's box asking for the key and I've tried leaving it as automatic - neither seems to make a difference)
[/LIST]
I'd be grateful for any help that lets me get this working!

---

### Post by cmnorton on 2008-01-02
Assuming you can log into the router and turn on/turn off wep encryption, then

Are you using network-manager to set up your connection?

When you set up the network and give the network name, what kind of passphrase are you selecting?

If you translated your wep-phrase into hex, then tell network-manager it's a 64/128-bit Hex (type).

That should get you connected.

---

### Post by ugm6hr on 2008-01-02
Couple of things to let us know.  

How many digits is your WPA code?  If it is less than 63 digits/letters. then try the following command (obviously substituting your own ssid / password):
```
wpa_passphrase *ssid* *password*
```
This should output something like:
```
network={
        ssid="ssid"
        #psk="password"
        psk=44116ea881531996d8a23af58b376d70f196057429c258f529577a26e727ec1b
}
```

Then try connecting again using the code after psk= as your WPA password.

To explain - Network Manager seems only able to use HEX WPA keys (not ASCII), and the ability to automatically convert has been left out (unlike in Wicd and Windows).  *wpa_passphrase* converts from ASCII to HEX manually for you.

If that doesn't work, post the output from the following commands:
```
lshw -C network
lsusb -v
```

---

### Post by majabl on 2008-01-02
> **cmnorton said:**
> Assuming you can log into the router and turn on/turn off wep encryption, then

Are you using network-manager to set up your connection?

When you set up the network and give the network name, what kind of passphrase are you selecting?

If you translated your wep-phrase into hex, then tell network-manager it's a 64/128-bit Hex (type).

That should get you connected.

Thanks for your response! :)  But still not connected. :(

I am able to log into the router with my work laptop to change settings.  This is using the standard Speedtouch 'software' that I access through my web browser.  I'd rather use WPA rather than WEP because it's more secure, and WPA is what I have been using with my Windows XP setup for years without any problem.

The passphrase is hex, I assume - all ten of its digits are hexadecimal numbers, at least.  I tried changing the router's settings from WPA to WEP but this didn't work to get Ubuntu connecting to it.  If anything it seemed worse - when inputting the password relevant to my network there's an option for WPA Personal and one for LEAP (whatever that is), but there's not one at all for WEP.

---

### Post by majabl on 2008-01-02
Thanks for the response. :)

> **ugm6hr said:**
> Couple of things to let us know.  

How many digits is your WPA code?  If it is less than 63 digits/letters. then try the following command (obviously substituting your own ssid / password):
```
wpa_passphrase *ssid* *password*
```
This should output something like:
```
network={
        ssid="ssid"
        #psk="password"
        psk=44116ea881531996d8a23af58b376d70f196057429c258f529577a26e727ec1b
}
```

Then try connecting again using the code after psk= as your WPA password.

Output as expected, but even using that long WPA password resulted in me 'bouncing back' to the 'Wireless Network Key Required' window as before.

> **ugm6hr said:**
> 
If that doesn't work, post the output from the following commands:
```
lshw -C network
lsusb -v
```

Bit of a beast coming out from that second command!  I think the second item listed amidst its output is my USB wireless card.

```
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:2f:c0:af:a6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0e:2e:43:b6:81
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

```
ubuntu@ubuntu:~$ lsusb -v

Bus 005 Device 006: ID 126f:2168 TwinMOS Mobile Disk III
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x126f TwinMOS
  idProduct          0x2168 Mobile Disk III
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 005: ID 148f:2573 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 004: ID 0dda:2026 Integrated Circuit Solution, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0dda Integrated Circuit Solution, Inc.
  idProduct          0x2026 
  bcdDevice            1.4f
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
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
      iInterface              5 
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
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0606 
  bcdDevice            7.02
  iManufacturer           0 
  iProduct                1 
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
    MaxPower              100mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
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

Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc505 Cordless Mouse+Keyboard Receiver
  bcdDevice           17.21
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
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
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
          wDescriptorLength     190
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
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
```

---

### Post by ugm6hr on 2008-01-02
I think the problem is that you have a Ralink chipset USB wifi card.

There are often conflicts between the various rt (ralink) drivers for Linux which result in multiple drivers being loaded.  There are some serialmonkey open source drivers that apparently work better:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Unfortunately that won't help from the LiveCD.  I have no idea if is possible from the LiveCD to connect because the Ra drivers do not use wpasupplicant (which I think is default in Network Manager).  Wicd might be a better option, but it cannot be installed without installing Ubuntu first (I think).

This is a pretty informative guide: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by majabl on 2008-01-04
> **ugm6hr said:**
> I think the problem is that you have a Ralink chipset USB wifi card.

There are often conflicts between the various rt (ralink) drivers for Linux which result in multiple drivers being loaded.  There are some serialmonkey open source drivers that apparently work better:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Unfortunately that won't help from the LiveCD.  I have no idea if is possible from the LiveCD to connect because the Ra drivers do not use wpasupplicant (which I think is default in Network Manager).  Wicd might be a better option, but it cannot be installed without installing Ubuntu first (I think).

This is a pretty informative guide: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Thanks again.  Looks like I'll be waiting until this is resolved (if it is resolved) in a future release - with my Ubuntu I'm looking for something that will 'just work' with the minimum of prodding and poking beneath the bonnet!

(Or waiting until I live somewhere where the main phone socket and the computer are close enough together for cabling to be viable - yes, it's technically possible now, but the other half wouldn't stand for it! :))

---

