---
title: "Snapstream Firefly Remote"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Efros on 2007-04-14
Anyone had any success using this device with Ubuntu?

[img]http://www.htpc-gear.com/shop/images/firefly.jpg[/img]

---

### Post by TheKid965 on 2007-04-21
Following the instructions [here](https://help.ubuntu.com/community/Install_Lirc_Feisty) got my newly-acquired Firefly remote to work in Feisty.  No real extra effort on my part beyond just going step by step down the document. 

I haven't used many PC remotes; the only other one was a simple Creative credit card-size thing that came with my Audigy 4, but that one works only in Windows as far as I can tell (all attempts to get lirc to recognize it have failed utterly).  With that said, I like the Firefly for its strong RF signal, plus the fact it *feels* like a good solid remote in my hand.  (The importance of this factor cannot be understated.)  The only thing is, not *all* the buttons work, and I can't seem to find any simple way to configure them to do what I want.  (Example: I want MythTV to start up when I press the logo button, but if there are instructions for how to do so, I'm not finding them.)

...Any ideas?

---

### Post by Efros on 2007-04-22
None mate, you have gfot way further than I have, I will follow your link and I'll let you know if I find anything.

---

### Post by nigel502 on 2007-04-29
so after following this did you get this to work? Did you happen to record your steps?

---

### Post by ghat on 2008-01-29
hi

I have tried and tried this with Ubuntu Gutsy and I am not able to get it working....

```

root@desktop:~# lsmod | grep lirc
lirc_atiusb            19360  0 
lirc_dev               15860  1 lirc_atiusb
usbcore               138632  8 lirc_atiusb,hci_usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

root@desktop:~# udevinfo -a -p $(udevinfo -q path -n /dev/lirc0)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/lirc/lirc0':
    KERNEL=="lirc0"
    SUBSYSTEM=="lirc"
    DRIVER==""
    ATTR{dev}=="61:0"

  looking at parent device '/devices/pci0000:00/0000:00:0c.0/usb3/3-2':
    KERNELS=="3-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="2"
    ATTRS{busnum}=="3"
    ATTRS{speed}=="1.5"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="0008"
    ATTRS{idVendor}=="0bc7"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{bmAttributes}=="80"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:257"

  looking at parent device '/devices/pci0000:00/0000:00:0c.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:0c.0"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic ohci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="3"
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

  looking at parent device '/devices/pci0000:00/0000:00:0c.0':
    KERNELS=="0000:00:0c.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{enable}=="1"
    ATTRS{modalias}=="pci:v00001033d00000035sv00003083sd00000035bc0Csc03i10"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="17"
    ATTRS{class}=="0x0c0310"
    ATTRS{subsystem_device}=="0x0035"
    ATTRS{subsystem_vendor}=="0x3083"
    ATTRS{device}=="0x0035"
    ATTRS{vendor}=="0x1033"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""


```

here is the config file
```

root@desktop:~# ls -l /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-01-28 22:59 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-01-28 22:59 /dev/lircd
root@desktop:~# irw

root@desktop:~# cat /etc/lirc/hardware.conf 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Snapstream X10 RF"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_atiusb"

# Default configuration files for your hardware if any
LIRCD_CONF="atiusb/lircd.conf.atiusb"
LIRCMD_CONF=""
root@desktop:~# 

```

Can anybody help!!!

I am using Ubuntu 7.10 (Gutsy) updated to Jan 25th at least... 

Ghat

---

