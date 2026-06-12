---
title: "Big Problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by aritrakundu on 2008-04-01
In order to use USB-Serial adapter I have to first create .rule file so that the device appears as ttyUSB$ when I type ls /dev. It appears when I plug the adapter. But when I set the minicom and try to open it gives the following message

**minicom: cannot open /dev/ttyUSB4: No such device or address**

My rule file is as follows:
# USB-Serial adapter ISIP
SUBSYSTEM=="usb_endpoint", ATTR{type}=="Bulk", ATTR{dev}=="254:7", NAME="ttyUSB4"
SUBSYSTEM=="usb_endpoint", SUBSYSTEMS=="usb", ATTRS{idProduct}=="5523", ATTRS{idVendor}=="4348", NAME="ttyUSB4", GROUP="dialout"

I have created this rule file from the following:

a# udevinfo -a -p $(udevinfo -q path -n /dev/usbdev1.5_ep82)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/usb_endpoint/usbdev1.5_ep82':
    KERNEL=="usbdev1.5_ep82"
    SUBSYSTEM=="usb_endpoint"
    DRIVER==""
    ATTR{direction}=="in"
    ATTR{type}=="Bulk"
    ATTR{interval}=="0ms"
    ATTR{wMaxPacketSize}=="0020"
    ATTR{bInterval}=="00"
    ATTR{bmAttributes}=="02"
    ATTR{bEndpointAddress}=="82"
    ATTR{bLength}=="07"
    ATTR{dev}=="254:7"

  looking at parent device '/devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS==""
    ATTRS{modalias}=="usb:v4348p5523d0250dcFFdsc00dp00icFFisc01ip02"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:07.2/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="USB-SER_"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="5"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="ff"
    ATTRS{bcdDevice}=="0250"
    ATTRS{idProduct}=="5523"
    ATTRS{idVendor}=="4348"
    ATTRS{bMaxPower}==" 78mA"
    ATTRS{bmAttributes}=="80"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:4"

  looking at parent device '/devices/pci0000:00/0000:00:07.2/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:07.2"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic uhci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:0"

  looking at parent device '/devices/pci0000:00/0000:00:07.2':
    KERNELS=="0000:00:07.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{enable}=="1"
    ATTRS{modalias}=="pci:v00008086d00007112sv000015ADsd00001976bc0Csc03i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="16"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x1976"
    ATTRS{subsystem_vendor}=="0x15ad"
    ATTRS{device}=="0x7112"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""


Please help me .

---

### Post by LowSky on 2008-04-01
> ```
looking at parent device '/devices/pci0000:00':
KERNELS=="pci0000:00"
SUBSYSTEMS==""
DRIVERS==""
ATTRS{uevent}==""

```

what is the cable attatch to? From what this says its connected to nothing

---

### Post by aritrakundu on 2008-04-01
Well ,the I was trying to perform a serial communication between 2 PC's. The USB-Serial converters which I was using before were automatically listed as ttyUSB0/1 when I plugged them in the system. But those adapters somehow were not communicating in LINUX and even in the Hyperterminal of the windows. So I chose to use different USB-Serial adapters which works fine with the Hyperterminal but not in LINUX. The above mentioned adapters are one of those.

Do you think I have to first conect them and then see their udevinfo??

---

