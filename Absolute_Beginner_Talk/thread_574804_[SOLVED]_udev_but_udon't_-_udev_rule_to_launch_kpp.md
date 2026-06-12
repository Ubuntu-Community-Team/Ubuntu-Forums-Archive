---
title: "[SOLVED] udev but udon't - udev rule to launch kppp"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-10-13
So I have a shiny new Novatel U727 mobile broadband adapter in Feisty and it works great.  However I want it to launch my dialer program whenever I plug it in.  "This looks like a job for UDEV".   So I do a little investigative work and come up with this bit of info that I will use to create my udev rule-


```
dad@mocal:~/Desktop$ udevinfo -a -p /sys/class/usb_device/usbdev1.3/device

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1':
    KERNEL=="1-1"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{serial}=="091050393811000"
    ATTR{product}=="Novatel Wireless CDMA"
    ATTR{manufacturer}=="Novatel Wireless Inc."
    ATTR{maxchild}=="0"
    ATTR{version}==" 1.10"
    ATTR{devnum}=="3"
    ATTR{speed}=="12"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{bNumConfigurations}=="1"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceClass}=="00"
    ATTR{bcdDevice}=="0000"
    ATTR{idProduct}=="4100"
    ATTR{idVendor}=="1410"
    ATTR{bMaxPower}=="500mA"
    ATTR{bmAttributes}=="a0"
    ATTR{bConfigurationValue}=="1"
    ATTR{bNumInterfaces}==" 5"
    ATTR{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.20-16-generic uhci_hcd"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
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

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d000024C2sv00000E11sd00000058bc0Csc03i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="10"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x0058"
    ATTRS{subsystem_vendor}=="0x0e11"
    ATTRS{device}=="0x24c2"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

And I come up with this bit to launch kppp:

```
# connect via kppp on insert/discovery

ACTION=="ADD", SUBSYSTEM=="usb", ATTR{product}=="Novatel Wireless CDMA", DRIVER=="usb",  RUN+="/usr/bin/kppp -c Sprint_EvDO"
```

But it hasn't worked yet.  The run command does work if I drop it into the command line, so I'm guessing my conditions aren't working.  The filename is 81-sprint.rules in /etc/udev/rules.d.

Any ideas?  When I plug the device in it first exposes a scsi device that I must eject before the wireless card is visible.  That is my next challenge-- to automatically eject /dev/sr1, but that is for later.  I'd like to get this worked out.  Any gurus out there than can give me some guidance?  I'd read the man page and other stuff and it looks like it should work, but obviously has not.

Thanks in advance.

---

### Post by milosz.galazka on 2007-10-13
Check */var/log/messages* for errors.

kppp require X window system to run.
But you could check
```
DISPLAY=:0 /usr/bin/kppp -c Sprint_EvDO
```

To check it just enter into your desktop manager (kde/gnome/...) then switch to text console (like ALT+CTRL+F1 or from menu) and run it then switch back (like ALT+CTRL+F7 for example) and you will see it. But X window system must be running and you logged in.
So maybe it should look like
```
su YOURUSERNAME -c 'DISPLAY=:0 /usr/bin/kppp -c Sprint_EvDO' 
```

---

### Post by lazyart on 2007-10-13
Well, since I'm in the GUI before I plug in the device I know X is running.  The log shows when I launch the connection manually, so for whatever reason I am not catching the device through the udev rule.

---

### Post by milosz.galazka on 2007-10-13
Yes you are in GUI but if udev tries to run command then it is run by user (as I think) root  in *plain environment*.

Could you post that error message? Maybe someone will know answer...

---

### Post by lazyart on 2007-10-13
no message, nothing in the logs to suggest that the rule is being executed.

---

### Post by milosz.galazka on 2007-10-13
I am trying to test how this stuff work :)

EDIT:
In this setup inserting USB Card Reader from GEMPLUS executes kppp at user desktop. I know that it looks weird :P

I created file */etc/udev/rules.d/10-local.rules* :
```
SUBSYSTEM=="usb",ATTR{product}=="GEMPC430, USB Card Reader from GEMPLUS",RUN+="/bin/su milosz -c '/etc/udev/gemplus.sh'"
```
Then I created script */etc/udev/gemplus.sh* :
```
#!/bin/sh
DISPLAY=:0 /usr/bin/kppp -c TEST
```
Then simply
```
chmod +x /etc/udev/rules.d/10-local.rules
chmod +x /etc/udev/gemplus.sh
/etc/init.d/udev restart
```
 
Then I attached device and ... it worked :) Hope that will help you...

---

### Post by lazyart on 2007-10-13
can you show me the udevinfo output you based your rules line from?  Maybe I'm missing something real simple here.  I tried making it into a script like you did called the script instead of the file directly.  Made it executable and tested it from my home before copying it to /etc/udev, but still no go.

---

### Post by milosz.galazka on 2007-10-14
```
 udevinfo -a -p /sys/class/usb_device/usbdev3.11/device

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.2/usb3/3-1':
    KERNEL=="3-1"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{product}=="GEMPC430, USB Card Reader from GEMPLUS"
    ATTR{manufacturer}=="GEMPLUS"
    ATTR{quirks}=="0x0"
    ATTR{maxchild}=="0"
    ATTR{version}==" 1.10"
    ATTR{devnum}=="11"
    ATTR{busnum}=="3"
    ATTR{speed}=="12"
    ATTR{bMaxPacketSize0}=="8"
    ATTR{bNumConfigurations}=="1"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceClass}=="00"
    ATTR{bcdDevice}=="0100"
    ATTR{idProduct}=="0430"
    ATTR{idVendor}=="08e6"
    ATTR{bMaxPower}=="100mA"
    ATTR{bmAttributes}=="80"
    ATTR{bConfigurationValue}=="1"
    ATTR{bNumInterfaces}==" 1"
    ATTR{configuration}==""
    ATTR{dev}=="189:266"

  looking at parent device '/devices/pci0000:00/0000:00:1d.2/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1d.2"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-386 uhci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="3"
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
    ATTRS{dev}=="189:256"

  looking at parent device '/devices/pci0000:00/0000:00:1d.2':
    KERNELS=="0000:00:1d.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d0000265Asv000014C0sd00000012bc0Csc03i00"
    ATTRS{local_cpus}=="1"
    ATTRS{irq}=="20"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x0012"
    ATTRS{subsystem_vendor}=="0x14c0"
    ATTRS{device}=="0x265a"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""
```

I used only 3 parameters to choose subsystem, device and command in udev. I just realized that I forgot about action but if I added it then it stopped working.

---

### Post by lazyart on 2007-10-14
Hmm... still having no luck.  When I plug in the device it exposes three items.  I decided to key off of the last device, a card reader, since I'm getting nowhere.  udevinfo says:```

udevinfo -a -p /sys/class/scsi_generic/sg2/device

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.4/host3/target3:0:0/3:0:0:0':
    KERNEL=="3:0:0:0"
    SUBSYSTEM=="scsi"
    DRIVER=="sd"
    ATTR{ioerr_cnt}=="0xa339"
    ATTR{iodone_cnt}=="0xa33a"
    ATTR{iorequest_cnt}=="0xa33a"
    ATTR{iocounterbits}=="32"
    ATTR{timeout}=="30"
    ATTR{state}=="running"
    ATTR{rev}=="2.31"
    ATTR{model}=="MMC Storage     "
    ATTR{vendor}=="Novatel "
    ATTR{scsi_level}=="3"
    ATTR{type}=="0"
    ATTR{queue_type}=="none"
    ATTR{queue_depth}=="1"
    ATTR{device_blocked}=="0"
    ATTR{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.4/host3/target3:0:0':
    KERNELS=="target3:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.4/host3':
    KERNELS=="host3"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.4':
    KERNELS=="1-1:1.4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{modalias}=="usb:v1410p4100d0000dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="04"

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="091050393811000"
    ATTRS{product}=="Novatel Wireless CDMA"
    ATTRS{manufacturer}=="Novatel Wireless Inc."
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="3"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0000"
    ATTRS{idProduct}=="4100"
    ATTRS{idVendor}=="1410"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 5"
    ATTRS{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:1d.0"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.20-16-generic uhci_hcd"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
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

  looking at parent device '/devices/pci0000:00/0000:00:1d.0':
    KERNELS=="0000:00:1d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d000024C2sv00000E11sd00000058bc0Csc03i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="10"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x0058"
    ATTRS{subsystem_vendor}=="0x0e11"
    ATTRS{device}=="0x24c2"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
So to keep things simple, I use the subsystem and vendor and create```
SUBSYSTEM=="scsi", ATTR{vendor}=="Novatel ", RUN+="/etc/udev/launch_kppp.sh"
```

launch_kppp.sh:```
#!/bin/sh
DISPLAY=:0 /usr/bin/kppp -c Sprint_EvDO 
```

Does something look wrong?

---

### Post by milosz.galazka on 2007-10-14
Maybe
```
SUBSYSTEM=="scsi", ATTR{vendor}=="Novatel ", RUN+="su YOURUSERNAME -c '/etc/udev/launch_kppp.sh'"
```
Do not forget to restart udev.

---

### Post by lazyart on 2007-10-14
In all the tutorials and documentation online I never saw anything to suggest that the script should be run as the user.  Worked like a champ.  Thanks a million.

The other bit about this device is that when it is first connected it exposes a CDROM that has to be ejected before it exposes the broadband adapter.  I'll try to add that to the same rules files. 

Again, thanks. :)

---

