---
title: "UE100 evdo modem not getting detected"
date: 2012-09-15
forum: Any Other OS
---

### Post by jasonbx on 2012-09-15
Hi,

I cannot get my UE100 evdo modem to work on ubuntu 12.04 (on AMD turion 64 bit). 
Here's the dmesg log after plugging in the modem, which goes into a loop

> 
[   69.896055] usb 2-3: new full-speed USB device number 4 using ohci_hcd
[   73.624346] usb 2-3: USB disconnect, device number 4
[   75.700073] usb 2-3: new full-speed USB device number 5 using ohci_hcd
[   75.915709] scsi5 : usb-storage 2-3:1.0
[   80.906675] usb 2-3: USB disconnect, device number 5
[   81.396080] usb 2-3: new full-speed USB device number 6 using ohci_hcd
[   85.124335] usb 2-3: USB disconnect, device number 6
...
...
...
[  145.404390] usb 2-3: USB disconnect, device number 16
[  147.480102] usb 2-3: new full-speed USB device number 17 using ohci_hcd
[  147.697068] scsi11 : usb-storage 2-3:1.0
[  152.683577] usb 2-3: USB disconnect, device number 17
[  153.224144] usb 2-3: new full-speed USB device number 18 using ohci_hcd
[  156.952344] usb 2-3: USB disconnect, device number 18
[  159.028087] usb 2-3: new full-speed USB device number 19 using ohci_hcd
[  159.243859] scsi12 : usb-storage 2-3:1.0



Output from /var/log/syslog

> Sep 15 23:54:25 mvp kernel: [   64.388057] usb 2-3: new full-speed USB device number 3 using ohci_hcd
Sep 15 23:54:26 mvp mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:26 mvp mtp-probe: bus: 2, device: 3 was not an MTP device
Sep 15 23:54:26 mvp kernel: [   64.613039] Initializing USB Mass Storage driver...
Sep 15 23:54:26 mvp kernel: [   64.614335] scsi4 : usb-storage 2-3:1.0
Sep 15 23:54:26 mvp kernel: [   64.614515] usbcore: registered new interface driver usb-storage
Sep 15 23:54:26 mvp kernel: [   64.614518] USB Mass Storage support registered.
Sep 15 23:54:26 mvp kernel: [   64.616979] usbcore: registered new interface driver uas
Sep 15 23:54:30 mvp kernel: [   69.344290] usb 2-3: USB disconnect, device number 3
Sep 15 23:54:31 mvp kernel: [   69.896055] usb 2-3: new full-speed USB device number 4 using ohci_hcd
Sep 15 23:54:31 mvp mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:31 mvp mtp-probe: bus: 2, device: 4 was not an MTP device
Sep 15 23:54:35 mvp kernel: [   73.624346] usb 2-3: USB disconnect, device number 4
Sep 15 23:54:37 mvp kernel: [   75.700073] usb 2-3: new full-speed USB device number 5 using ohci_hcd
Sep 15 23:54:37 mvp kernel: [   75.915709] scsi5 : usb-storage 2-3:1.0
Sep 15 23:54:37 mvp mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:37 mvp mtp-probe: bus: 2, device: 5 was not an MTP device
Sep 15 23:54:42 mvp kernel: [   80.906675] usb 2-3: USB disconnect, device number 5
Sep 15 23:54:42 mvp kernel: [   81.396080] usb 2-3: new full-speed USB device number 6 using ohci_hcd
Sep 15 23:54:43 mvp mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:43 mvp mtp-probe: bus: 2, device: 6 was not an MTP device
Sep 15 23:54:46 mvp kernel: [   85.124335] usb 2-3: USB disconnect, device number 6
Sep 15 23:54:48 mvp kernel: [   87.200199] usb 2-3: new full-speed USB device number 7 using ohci_hcd
Sep 15 23:54:48 mvp kernel: [   87.415721] scsi6 : usb-storage 2-3:1.0
Sep 15 23:54:48 mvp mtp-probe: checking bus 2, device 7: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:48 mvp mtp-probe: bus: 2, device: 7 was not an MTP device
Sep 15 23:54:53 mvp kernel: [   92.407181] usb 2-3: USB disconnect, device number 7
Sep 15 23:54:54 mvp kernel: [   92.896104] usb 2-3: new full-speed USB device number 8 using ohci_hcd
Sep 15 23:54:54 mvp mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:54:54 mvp mtp-probe: bus: 2, device: 8 was not an MTP device
Sep 15 23:54:58 mvp kernel: [   96.624370] usb 2-3: USB disconnect, device number 8
Sep 15 23:55:00 mvp kernel: [   98.700083] usb 2-3: new full-speed USB device number 9 using ohci_hcd
Sep 15 23:55:00 mvp kernel: [   98.915711] scsi7 : usb-storage 2-3:1.0
Sep 15 23:55:00 mvp mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:13.0/usb2/2-3"
Sep 15 23:55:00 mvp mtp-probe: bus: 2, device: 9 was not an MTP device
Sep 15 23:55:05 mvp kernel: [  103.903048] usb 2-3: USB disconnect, device number 9
Sep 15 23:55:05 mvp kernel: [  104.392093] usb 2-3: new full-speed USB device number 10 using ohci_hcd
lsusb output

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a100 Suyin Corp. Acer OrbiCam
Bus 002 Device 026: ID 15eb:1231  
0x15eb is the vendor id and 0x1231 is the product id.

The usb_modeswitch/usb_modeswitch_dispatcher is not working correctly?

Can someone please provide any pointers on how to make this modem work?

---

### Post by pdc on 2012-09-16
I see you have also posted on the Mint forum 

[http://forums.linuxmint.com/viewtopic.php?f=49&t=112553&p=628822#p628822](http://forums.linuxmint.com/viewtopic.php?f=49&t=112553&p=628822#p628822)

I left a reply there

if you subscribe to threads, you can get an email when there is a reply

---

