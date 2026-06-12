---
title: "Usb mass not working"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by kingtim21 on 2008-03-12
My usb 500gb is not show up at all.It use to work. Ever since i went to my friends house it was working.

When i was there he share(shared with windows xp pro sev pack 2) the it on his network so we can copy it from different computer 

it did work when i got home
this shows up system log viewer

Mar 12 21:23:15 dart620-desktop kernel: [ 5851.436000] usb 5-4: new high speed USB device using ehci_hcd and address 8
Mar 12 21:23:15 dart620-desktop kernel: [ 5851.568000] usb 5-4: configuration #1 chosen from 1 choice
Mar 12 21:23:15 dart620-desktop kernel: [ 5851.572000] scsi6 : SCSI emulation for USB Mass Storage devices
Mar 12 21:23:15 dart620-desktop kernel: [ 5851.572000] usb-storage: device found at 8
Mar 12 21:23:15 dart620-desktop kernel: [ 5851.572000] usb-storage: waiting for device to settle before scanning
Mar 12 21:23:15 dart620-desktop NetworkManager: <debug> [1205317395.979154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6'). 
Mar 12 21:23:17 dart620-desktop NetworkManager: <debug> [1205317397.727087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0'). 
Mar 12 21:23:18 dart620-desktop NetworkManager: <debug> [1205317398.122951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_usbraw'). 
Mar 12 21:23:20 dart620-desktop kernel: [ 5856.572000] usb-storage: device scan complete
Mar 12 21:23:20 dart620-desktop kernel: [ 5856.576000] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Mar 12 21:23:20 dart620-desktop kernel: [ 5856.588000] sd 6:0:0:0: [sda] Attached SCSI disk
Mar 12 21:23:20 dart620-desktop kernel: [ 5856.588000] sd 6:0:0:0: Attached scsi generic sg0 type 0
Mar 12 21:23:20 dart620-desktop NetworkManager: <debug> [1205317400.718746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host'). 
Mar 12 21:23:20 dart620-desktop NetworkManager: <debug> [1205317400.731087] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0'). 
Mar 12 21:23:20 dart620-desktop NetworkManager: <debug> [1205317400.742206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Mar 12 21:23:20 dart620-desktop NetworkManager: <debug> [1205317400.973500] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_JMicron_USB_to_ATA_ATAPI_Bridge_152D203380B6_0_0'). 
Mar 12 21:46:39 dart620-desktop -- MARK -- 

it show up in Device Manager

[IMG]http://imageiso.com/out.php/i16275_devmanusb.jpeg[/IMG]

pls help

---

### Post by Mick8882003 on 2008-03-12
Ive had the same trouble with my usb disk, I am thinking that you need to "safely remove hardware" on a windows system before it will work again,

---

### Post by kingtim21 on 2008-03-12
on windows it just shows up as mass storage device  doesn't show up

---

### Post by jan quark on 2008-03-12
> on windows it just shows up as mass storage device doesn't show up
:confused:

does is show up or does it not show up, that is here the question....

can you safely remove it in windows?

---

### Post by intel on 2008-03-12
go to the menu on top of the screen
open "computer" option

find USB drive
righ-click
select "mount"

tell us the error if any

---

### Post by kingtim21 on 2008-03-12
> **jan quark said:**
> :confused:

does is show up or does it not show up, that is here the question....

can you safely remove it in windows?

i can safely remove in windows

---

### Post by kingtim21 on 2008-03-12
> **intel said:**
> go to the menu on top of the screen
open "computer" option

find USB drive
righ-click
select "mount"

tell us the error if any

it does not show up in computer

---

### Post by MasterJS on 2008-03-12
There is a possiblity that windows wants to run a Check Disk on it. Try rebooting with it still connected and windows might run the check disk. And then it could be fixed. But always remember to use the safely remove hardware.

---

### Post by kingtim21 on 2008-03-13
> **MasterJS said:**
> There is a possiblity that windows wants to run a Check Disk on it. Try rebooting with it still connected and windows might run the check disk. And then it could be fixed. But always remember to use the safely remove hardware.

I did that but it didn't do  a disk check

---

