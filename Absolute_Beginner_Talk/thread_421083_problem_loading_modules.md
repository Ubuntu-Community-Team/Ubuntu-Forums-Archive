---
title: "problem loading modules"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by pecoronas on 2007-04-24
hello, i'm using ubuntu 7.04

when i try to load modules that are located in this directory:

/lib/modules/2.6.20-15-generic/kernel/drivers/usb/atm/

i always have this error, it happens ONLY with modules in the atm directory, all other modules load normally:
```

root@okapi-desktop:/home/okapi/Desktop# modprobe ueagle-atm
FATAL: Error inserting ueagle_atm (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/atm/ueagle-atm.ko): Unknown symbol in module, or unknown parameter (see dmesg)

root@okapi-desktop:/home/okapi/Desktop# modprobe cxacru
FATAL: Error inserting cxacru (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/atm/cxacru.ko): Unknown symbol in module, or unknown parameter (see dmesg)

root@okapi-desktop:/home/okapi/Desktop# modprobe speedtch
FATAL: Error inserting speedtch (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/atm/speedtch.ko): Unknown symbol in module, or unknown parameter (see dmesg)

root@okapi-desktop:/home/okapi/Desktop# modprobe xusbatm
FATAL: Error inserting xusbatm (/lib/modules/2.6.20-15-generic/kernel/drivers/usb/atm/xusbatm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

so what's wrong with my atm directory?:confused:

---

### Post by speeves on 2007-04-24
Hi,

Can you post the contents of dmesg after you try to load your modules?

thanks,

---

### Post by xyz on 2007-04-24
Run
```
 dmesg
```
and see what's wrong or post output.

---

### Post by pecoronas on 2007-04-24
thank you for your help!
here's some examples, numbers change evrytime...

```

root@okapi-desktop:/home/okapi/Desktop# dmesg | grep ueagle
[   51.778631] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[   51.778922] ueagle_atm: Unknown symbol usbatm_usb_probe
[   51.809235] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[   51.809526] ueagle_atm: Unknown symbol usbatm_usb_probe
[   52.034454] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[   52.034758] ueagle_atm: Unknown symbol usbatm_usb_probe
[ 1085.203318] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[ 1085.203661] ueagle_atm: Unknown symbol usbatm_usb_probe
[ 1171.986223] ueagle_atm: Unknown symbol usbatm_usb_disconnect
[ 1171.986585] ueagle_atm: Unknown symbol usbatm_usb_probe

root@okapi-desktop:/home/okapi/Desktop# dmesg | grep cxacru
[ 1984.101345] cxacru: Unknown symbol usbatm_usb_disconnect
[ 1984.101531] cxacru: Unknown symbol usbatm_usb_probe

root@okapi-desktop:/home/okapi/Desktop# dmesg | grep speedtch
[ 2015.434523] speedtch: Unknown symbol usbatm_usb_disconnect
[ 2015.434827] speedtch: Unknown symbol usbatm_usb_probe
```

---

### Post by xyz on 2007-04-24
[SEE LAST POST HERE]("http://ubuntuforums.org/archive/index.php/t-242789.html")...might help.
or
[THIS]("http://atm.eagle-usb.org/wakka.php?wiki=PagePrincipaleEn")

---

