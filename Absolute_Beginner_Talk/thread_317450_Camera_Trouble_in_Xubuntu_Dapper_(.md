---
title: "Camera Trouble in Xubuntu Dapper :("
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by koolkid64us on 2006-12-12
I can't seem to gain any access to my Kodak EasyShare CX6230 camera.

```
chris@Chris:~$ for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-0:1.0':
    KERNEL=="1-0:1.0"
    SUBSYSTEM=="unknown"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="09"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="00"
    SYSFS{bInterfaceSubClass}=="00"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{modalias}=="usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1':
    KERNEL=="1-1"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="16"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0100"
    SYSFS{bmAttributes}=="c0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="5"
    SYSFS{idProduct}=="0573"
    SYSFS{idVendor}=="040a"
    SYSFS{manufacturer}=="Eastman Kodak Company"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="KODAK EasyShare CX6230 Zoom Digital Camera"
    SYSFS{speed}=="12"
    SYSFS{version}==" 2.00"


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-1/1-1:1.0':
    KERNEL=="1-1:1.0"
    SUBSYSTEM=="unknown"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="06"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="01"
    SYSFS{bInterfaceSubClass}=="01"
    SYSFS{bNumEndpoints}=="03"
    SYSFS{modalias}=="usb:v040Ap0573d0100dc00dsc00dp00ic06isc01ip01"


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-2':
    KERNEL=="1-2"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bMaxPower}=="500mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="1040"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="3"
    SYSFS{idProduct}=="4240"
    SYSFS{idVendor}=="0846"
    SYSFS{manufacturer}=="GlobespanVirata"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="NETGEAR WG111"
    SYSFS{serial}=="3887-0000"
    SYSFS{speed}=="12"
    SYSFS{version}==" 2.00"


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0':
    KERNEL=="1-2:1.0"
    SUBSYSTEM=="unknown"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="ff"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="ff"
    SYSFS{bInterfaceSubClass}=="ff"
    SYSFS{bNumEndpoints}=="05"
    SYSFS{modalias}=="usb:v0846p4240d1040dc00dsc00dp00icFFiscFFipFF"


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at class device '/sys/devices/pci0000:00/0000:00:07.2/usb1':
    KERNEL=="usb1"
    SUBSYSTEM=="unknown"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0206"
    SYSFS{bmAttributes}=="c0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="1"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{manufacturer}=="Linux 2.6.15-27-386 uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{serial}=="0000:00:07.2"
    SYSFS{speed}=="12"
    SYSFS{version}==" 1.10"

chris@Chris:~$ dmesg | tail
[  107.460735] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  112.692992] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  112.693022] hdc: drive_cmd: error=0x04 { AbortedCommand }
[  112.693035] ide: failed opcode was: 0xec
[  117.105015] Non-volatile memory driver v1.2
[  117.140265] input: /usr/sbin/thinkpad-keys as /class/input/input3
[  172.237336] usb 1-1: USB disconnect, address 2
[  191.682639] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  216.079395] usb 1-1: USB disconnect, address 4
[  397.286617] usb 1-1: new full speed USB device using uhci_hcd and address 5

```

According to that, my camera is recognized, but not doing anything, could anyone help?:-k

---

### Post by ingo on 2006-12-14
how are you trying to access it? 'cos if it's there... tried digikam?

---

### Post by marx2k on 2006-12-14
My camera (Fujifilm) opens up as a USB drive and F-Spot Photo Manager automatically opens.  Did you check to see if your setup mounted the camera as a drive possibly?

---

