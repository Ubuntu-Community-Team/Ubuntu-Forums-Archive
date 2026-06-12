---
title: "Another USB issue...external hd and printer"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by maatghandi on 2005-11-27
I just installed 5.10 last night. Everything is working great, but I can't seem to get it to recognize either of my usb devices. Working on my hd, I edited fstab with..

/dev/sda1       /mnt/usbhd      vfat    user,umask=000 0 0

and I executed...

mount /dev/sda1 /mnt/usbhd

without errors. I created /mnt/usbhd before hand, and it exists. But nothing in the directory. /sys/block shows no sda blocks, nor are there any sda1 files in /dev. Also, mtab does not show that I mounted the hd, even though there were no errors when I executed mount.

I know the usb ports work, so I am lost from here :confused: 

Thanks
Jerome

---

### Post by EC-Rider on 2005-11-27
Hi Jerome,

What happens when you take this USB device out and plug it in on an another port? Is the OS recognizing this device than? Hopefully it does and you can read some parameters from it to add to fstab.

Regards,
Eric

---

### Post by maatghandi on 2005-11-27
No, doesn't work. Either for my printer or hd. Both devices are on.

---

### Post by maatghandi on 2005-11-27
Do I need to mess with udev rules? I am reading a page on this, and I used

# udevinfo -a -p /sys/block/hdd
device '/sys/block/hdd' has major:minor 22:64
  looking at class device '/sys/block/hdd':
    SUBSYSTEM=="block"
    SYSFS{dev}=="22:64"
    SYSFS{range}=="1"
    SYSFS{removable}=="1"
    SYSFS{size}=="8388604"
    SYSFS{stat}=="       0        0        0        0        0        0        0        0        0        0        0"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:07.1/ide1/1.1':
    BUS=="ide"
    ID=="1.1"
    DRIVER=="ide-cdrom"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:07.1/ide1':
    BUS==""
    ID=="ide1"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:07.1':
    BUS=="pci"
    ID=="0000:00:07.1"
    DRIVER=="VIA_IDE"
    SYSFS{class}=="0x01018a"
    SYSFS{device}=="0x0571"
    SYSFS{irq}=="0"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v00001106d00000571sv00000000sd00000000bc01sc01i8a"
    SYSFS{subsystem_device}=="0x0000"
    SYSFS{subsystem_vendor}=="0x0000"
    SYSFS{vendor}=="0x1106"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS==""
    ID=="pci0000:00"
    DRIVER=="unknown"

I have similar responses to hdc and hda, except the BUS is pci. I only have one internal ide hard drive. Why do all three of these come up with information? I am rather confused with this hole udev thing because Fedora had all sda blocks already allocated. Do I create them by writing a new rule in udev?

---

