---
title: "USB Drive sometimes mounted"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by tgrisier on 2007-04-30
I have found that in KDE my USB drive sometimes is mounted and sometimes not.  What makes this odd is that it always mounts in gnome and xfce.

Why does KDE seem picky as to when it mounts this drive?

---

### Post by compiledkernel on 2007-04-30
hmmm, question. 

When it isnt mounted or doesnt show as mounted can you open up a terminal and type 

lsusb -v 

and find the description of the USB drive in the list?

---

### Post by tgrisier on 2007-04-30
> **compiledkernel said:**
> hmmm, question. 

When it isnt mounted or doesnt show as mounted can you open up a terminal and type 

lsusb -v 

and find the description of the USB drive in the list?


Yeah, it seems to see it along with my mouse, keyboard cable modem and printer.


Here's the output of lsusb:

Bus 005 Device 002: ID 03f0:5611 Hewlett-Packard 
Bus 005 Device 006: ID 152d:2338  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 07b2:5101 Motorola BCS, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

---

### Post by compiledkernel on 2007-04-30
ok can you do a 

sudo lsusb -D 

the D switch should show the actual /dev being used. 

Once you determine that can you actually mount the proper /dev in a terminal?

---

### Post by tgrisier on 2007-04-30
ok, I must be doing something wrong here.  I put in the command (actually copy/pasted it) and here's the result.

tony@tony-desktop:~$ kdesu lsusb -D
kdesu: Unknown option '-D'.
kdesu: Use --help to get a list of available command line options.
tony@tony-desktop:~$ sudo lsusb -D
lsusb: option requires an argument -- D
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
tony@tony-desktop:~$

---

### Post by compiledkernel on 2007-04-30
herf, sorry. 

I meant 

kdesu lsusb -v 

verbose output should list the device.

---

### Post by tgrisier on 2007-04-30
Alright, here's the usb drive portion of that command.

Bus 005 Device 006: ID 152d:2338  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d 
  idProduct          0x2338 
  bcdDevice            1.00
  iManufacturer           1 JMicron
  iProduct                2 USB to ATA/ATAPI Bridge
  iSerial                 5 7CA851347551
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 MSC Bulk-Only Transfer
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


I'm not quite sure where to find the mount info from this.

---

### Post by gadfium on 2007-04-30
I don't know where you get the device name from in that list either. However, I have the same problem of my usb drive no longer automounting in KDE, but it works fine on a couple of Windows machines that I tried it with. My solution:

1. run 'udevmonitor' in a terminal (as root), plug in the device. You should see a series of lines such as:
add      /block/sdb/sdb1 (block)
This gives you the address you need: in my case, /dev/sdb1.

2. Create a directory in which to mount the key, eg. /media/usb
3. Mount it with 'mount /dev/sdb1 /media/usb'
4. Work with the key as normal
5. Unmount it when finished with 'umount /media/usb'

I gather from reading other threads here that the automounter when upgrading to Feisty is broken, so you may have to keep doing it manually until there's a fix.

---

### Post by gadfium on 2007-04-30
A slightly simpler method of mounting:

As normal user:

pmount /dev/sdb1 usbkey
--use the device, which will be mounted on /media/usbkey
pumount usbkey

---

### Post by tgrisier on 2007-05-01
Thanks, I'll give that a try.

---

### Post by tgrisier on 2007-05-01
> pmount /dev/sdb1 usbkey
--use the device, which will be mounted on /media/usbkey
pumount usbkey                                                                                                                                 

Worked like a charm.  Now, how would I make a script that would do this automagically.

---

