---
title: "SanDisk Cruzer Micro 4GB fails on large write"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by fourstarbeans on 2007-05-07
Hi all, when I plug in and mount my SanDisk Cruzer Micro on my 6.06 LTS (Dapper) machine and try to write a large file, I get some crazy errors! Like...

```
Apr 20 22:49:17 kernel: [17180097.316000] scsi2 : SCSI emulation for USB Mass Storage devices
Apr 20 22:49:22 kernel: [17180102.320000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 3.21
Apr 20 22:49:22 kernel: [17180102.320000]   Type:   Direct-Access                  ANSI SCSI revision: 02
Apr 20 22:49:22 kernel: [17180102.324000] SCSI device sda: 8027793 512-byte hdwr sectors (4110 MB)
Apr 20 22:49:22 kernel: [17180102.328000] sda: Write Protect is off
Apr 20 22:49:22 kernel: [17180102.340000] SCSI device sda: 8027793 512-byte hdwr sectors (4110 MB)
Apr 20 22:49:22 kernel: [17180102.340000] sda: Write Protect is off
Apr 20 22:49:22 kernel: [17180102.340000]  sda: sda1 sda2
Apr 20 22:49:22 kernel: [17180102.352000] sd 2:0:0:0: Attached scsi removable disk sda
Apr 20 22:49:22 kernel: [17180102.352000] sd 2:0:0:0: Attached scsi generic sg0 type 0
Apr 20 22:53:57 kernel: [17180377.220000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:54:27 kernel: [17180407.420000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:54:57 kernel: [17180437.620000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:55:27 kernel: [17180467.820000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:55:58 kernel: [17180498.020000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:55:58 kernel: [17180498.136000] sd 2:0:0:0: SCSI error: return code = 0x50000
Apr 20 22:55:58 kernel: [17180498.136000] end_request: I/O error, dev sda, sector 81766
Apr 20 22:55:58 kernel: [17180498.136000] lost page write due to I/O error on sda1
Apr 20 22:56:28 kernel: [17180528.224000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:56:58 kernel: [17180558.408000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:57:28 kernel: [17180588.592000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:57:58 kernel: [17180618.792000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:58:29 kernel: [17180648.992000] usb 1-1.1.4: reset full speed USB device using uhci_hcd and address 7
Apr 20 22:58:29 kernel: [17180649.104000] sd 2:0:0:0: SCSI error: return code = 0x50000
Apr 20 22:58:29 kernel: [17180649.104000] end_request: I/O error, dev sda, sector 81767
Apr 20 22:58:29 kernel: [17180649.104000] lost page write due to I/O error on sda1
```

I end up having to use fsck to fix a number of problems -- which continue to occur on successive boots of the OS.

This is the second SanDisk Cruzer Mini 4GB that I've had this issue with. I replaced the first one with one from another store because I thought it might be the USB stick that was causing the problem. But nope, same errors.

I've also tried different USB ports when copying the files. Same problem.

The only thing that seems to work is mounting the Ubuntu CD and the USB stick under Windows XP, and copying the files there. No problems with copying.

Any ideas?

---

### Post by tgalati4 on 2007-05-07
With the cruzer plugged in, post the output of:

lsusb -v

Is there a 4-way port that you are going through?

How was the disk originally formatted?

Did you try formatting it as ext2 using cfdisk?  Perhaps try formatting as 2 x 2GB partitions with FAT32.

---

### Post by fourstarbeans on 2007-05-07
Let me give that a shot.

---

### Post by tgalati4 on 2007-05-07
I have a 4GB Sandisk SD memory card in my phone.  I usually have it filled with music, videos and podcasts.  I simply drag and drop in nautilus or on my powerbook I use SyncTunes to load it from iTunes.  I've never had problems with it.  It probably uses the same SanDisk memory chip and controller.

I have not used a USB card reader, nor have I copied large (*.ISO) files.  Most of the files are only a few megs each.

With 4GB you could put Ubuntu on it.  Then you could boot off of your phone!

---

### Post by fourstarbeans on 2007-05-07
> **tgalati4 said:**
> With the cruzer plugged in, post the output of:

lsusb -v

Okay, That's ```
Bus 002 Device 001: ID 0000:0000
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
  iManufacturer           3 Linux 2.6.15-28-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1f.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc0
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 001 Device 007: ID 0781:5406 SanDisk Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0781 SanDisk Corp.
  idProduct          0x5406
  bcdDevice            0.10
  iManufacturer           1 SanDisk Corporation
  iProduct                2 U3 Cruzer Micro
  iSerial                 3 00001868XXXXXXXX
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
    MaxPower              100mA
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

Bus 001 Device 004: ID 0424:2602 Standard Microsystems Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0x2602
  bcdDevice            0.00
  iManufacturer           0
  iProduct                0
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
    MaxPower                2mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      1 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0xc1
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0103 power enable connect
   Port 4: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0x2228
  bcdDevice            4.44
  iManufacturer           1 Generic
  iProduct                2 Flash Card Reader
  iSerial                 3 26020128B005
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
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
      iInterface              0
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
        bInterval               0
        UNRECOGNIZED:  07 21 07 e8 03 fe ff
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

Bus 001 Device 002: ID 0424:2502 Standard Microsystems Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0x2502
  bcdDevice            0.01
  iManufacturer           0
  iProduct                0
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
    MaxPower                2mA
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
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0004
    Ganged power switching
    Compound device
    Ganged overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      1 milli Ampere
  DeviceRemovable    0x40
  PortPwrCtrlMask    0x72
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 001 Device 003: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x1204 DeskJet 930c
  bcdDevice            1.00
  iManufacturer           1 Hewlett-Packard
  iProduct                2 DeskJet 930C
  iSerial                 3 MY02S11012JJ
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      1 Unidirectional
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
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
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered

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
  iManufacturer           3 Linux 2.6.15-28-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1f.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
  DeviceRemovable    0xa8
  PortPwrCtrlMask    0x93
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0001
  Self Powered
```

> **tgalati4 said:**
> How was the disk originally formatted?

Like so...

```
# fdisk -l /dev/sda

Disk /dev/sda: 4110 MB, 4110230016 bytes
16 heads, 63 sectors/track, 7964 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1454      732784+   6  FAT16
/dev/sda2            1455        7964     3281040   83  Linux
```

> **tgalati4 said:**
> Is there a 4-way port that you are going through?

Hmm, I don't know about that, but I use a multifunction card reader which includes two USB ports. It's part of my Dell flat-panel monitor.

> **tgalati4 said:**
> Did you try formatting it as ext2 using cfdisk?  Perhaps try formatting as 2 x 2GB partitions with FAT32.

My goal was to [make a bootable USB drive as in this linked tutorial](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar). I used fdisk to format it as FAT16 and ext2 (as above in the fdisk -l output).

---

### Post by tgalati4 on 2007-05-07
Good observation.  Your built-in reader is really a hub because it provides extra USB ports.  It's possible that going through the extra hub is causing timing issues, especially with large files.  Also, realize that Nautilus will report that the file is transfered, but it really isn't.  It's just handwaving so that the operating system can continue to do something else.  In Windows, your machine will slow to a crawl waiting for I/O to finish.  With a multitasking operating system, the copy operation is pushed to the background.  If you eject or pull your flash stick before the copy is finished, it will corrupt the partition.  It could take 15-25 minutes to copy 4GB depending on how fast the write circuits are.  Remember, these are consumer devices, not professional memory cards that professional photographers use that write at 80X.

It's happened to me a few times, pulling a USB flash stick before a large copy operation was finished.

Is there are reason that you can't use a Live CD and just save your /home/yourusername to the USB stick?

This allows you to keep all of your data with you and it gives you more space.

Then leave the CD with the computer or keep a few in the car, backpack, locker.  CD's are cheap.

The problem with keeping the OS on the USB stick is that if the OS gets corrupt, it takes your data with it.  Also, because Linux does a lot of writebacks to /proc and /var/log, it can wear out your memory stick in a hurry.  Better to use if for static data, like  your /home files.

Next time you perform an *.iso copy:

df -h
 
Keep repeating the command (up arrow, then return) until you see that the /dev/sda partition is the expected size (~700MB).

Just because  you can do something, doesn't mean it's a good idea.  Damn Small Linux is designed to boot off of a USB.  The developers modified the kernel to reduce as many writebacks as possible and they slimed the operating system down to 50MB.  So it really depends on what you want to do.

---

