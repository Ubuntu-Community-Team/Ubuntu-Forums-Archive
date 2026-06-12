---
title: "Ubuntu 11.04 ASUS G74Sx USB 3.0 Support"
date: 2011-08-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Decessus0 on 2011-08-24
Hello, I have an ASUS G74Sx and am currently running Ubuntu 11.04 x64. I have a USB 3.0 port, however, it will not detect any media (1.1-3.0)

lsusb output:
```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1bcf:2885 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 13d3:3304 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It is recognized as a USB 3.0 device

lusb -v output for 3.0 device:
```
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.38-11-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:04:00.0
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
```

dmesg | grep usb output:
```
[    3.394482] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
```

I've tested a USB 3.0 External HDD, a USB 2.0 flash drive, a USB 2.0 keyboard and an old USB 1.1 keyboard, nothing recognizes.

---

### Post by force13 on 2011-08-25
I am also using The asus g74sx and im having the same issues, im sure these issues will be fixed as soon as they can, I know the g74 is new

---

### Post by flynx on 2011-09-06
Same problem on my Clevo W150HNQ.  
 
lsusb:
 
```
 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


```
 
Devices won't even charge from the 3.0 ports.

---

### Post by Gtandecki on 2011-09-16
Has this issue been solved? I have the exact same issue and exact same problems and exact computer. Windows 7 operates normally with my 3.0 port but in ubuntu its not seen at all and doesn't even seem to be powering up.

---

### Post by HerrRossi on 2011-09-30
Same system (G74SX), same problem here, no solution yet

---

### Post by ubersoft on 2011-09-30
It doesn't help with 11.04, but I have a G74S and its USB 3.0 port can detect media under Oneric. I don't know if it can achieve USB 3.0 speeds, but it can be used...

---

### Post by david_williams on 2011-10-12
I too have an ASUS G74Sx, and following the advice in a previous post, at 
[http://ubuntuforums.org/showthread.php?t=1680278](http://ubuntuforums.org/showthread.php?t=1680278)
I was able to get my Ubuntu 11.04 (x64) based system to at least "see" the USB3 port, but, not sure its treating it as USB3. I don't have any USB3 devices to test it, but, was glad to at least have a third USB2 port. In short, added 
pci=nomsi 
to the kernel options in GRUB boot file. 
I hope the link might also help others but, I have little idea what other effects "nomsi" option may have or what it "really" means.

---

### Post by HerrRossi on 2011-10-13
Changing grub the proposed way worked for me. USB port is active now. Seems to be fast as well. Copied 1gb to my usb3.0 32gb thumb drive at 40mb/s I think that might be usb 3.0 speed. 
Thanks!

---

### Post by Gtandecki on 2011-10-20
Update:

I have updated to the latest release of Ubuntu and found that my USB 3.0 port works but it only gets speeds of USB 2.0 at best. My fastest speed has been a little over 30 MB/sec. Using windows I often get 140 MB/sec. and more.

So if you just need the port to work the latest update will do it but if you want the speed you won't get it just by updating. Also, when I upgraded my wireless works without fail when it didn't before as well as my blue ray drive seems to work but need to test further. There are several other minor things that are now working much better but usb 3.0 speeds are not there as of yet.

---

### Post by Tjofalt on 2011-11-17
My USB 3.0 port is detected and works.

However, I get the same speed (according to Disk Utility) when the disk is plugged in to the USB 2 port(s), i.e. about 40MB/s.

Setup: Ubuntu 11.10, G74SX, WD500 passport, using original cable.

---

