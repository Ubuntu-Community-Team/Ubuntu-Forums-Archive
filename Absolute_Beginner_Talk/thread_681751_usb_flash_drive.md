---
title: "usb flash drive"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by vr76413 on 2008-01-29
I just plugged my USB flash drive to Ubuntu 7.10, and dont have any icon on the desktop. 
i did

# ls /media 

and i dont see any USB folders.

How do i access files and folders from USB drive ?

thanks
Ram K

---

### Post by amo-ej1 on 2008-01-29
could you past the final output lines of the 'dmesg' command ?

---

### Post by vr76413 on 2008-01-29
----------------------------------------------------------------------------------
[77116.379572] sd 6:0:0:1: [sdc] Sense not available.
[77116.379588] sd 6:0:0:1: [sdc] Write Protect is off
[77116.379592] sd 6:0:0:1: [sdc] Mode Sense: 00 00 00 00
[77116.379597] sd 6:0:0:1: [sdc] Assuming drive cache: write through
[77116.379646] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[77116.379690] sd 6:0:0:1: Attached scsi generic sg3 type 0
[77116.490678] usb 5-3: new high speed USB device using ehci_hcd and address 11
[77131.557051] usb 5-3: device descriptor read/64, error -110
[77146.727117] usb 5-3: device descriptor read/64, error -110
[77146.942463] usb 5-3: new high speed USB device using ehci_hcd and address 12
[77162.008831] usb 5-3: device descriptor read/64, error -110
[77177.178890] usb 5-3: device descriptor read/64, error -110
[77177.394243] usb 5-3: new high speed USB device using ehci_hcd and address 13
[77187.770821] usb 5-3: device not accepting address 13, error -110
[77187.882487] usb 5-3: new high speed USB device using ehci_hcd and address 14
[77198.259060] usb 5-3: device not accepting address 14, error -110

------------------------------------------------------------------------------------------------------------

thanks
Ram K

---

### Post by aeiah on 2008-01-29
that doesnt look too healthy. is there anything on the usb drive that's important? if not, try reformatting it. if there is, then you could try mounting it manually. you'll need to know what name  it is under in /dev/ (probably sda1 or something), then

mkdir usbmountlocation
mount /dev/sda1 usbmountlocation

---

### Post by vr76413 on 2008-01-29
still no luck.
I did format the usb flash drive on windows and plugged it back into ubuntu system.
any other ideas?

thanks
Ram K

---

### Post by vr76413 on 2008-01-31
any thoughts ?

thanks
Ram K

---

### Post by wolfen69 on 2008-01-31
plugin usb drive, open terminal and type
```
sudo fdisk -l
```
post output here.

---

### Post by seventhc on 2008-01-31
plug the usb in (ubuntu) run this in the terminal```
 fdisk -l
```I would also try this:
As a test I would boot back into windows and try writing data to the usb. See if it accepts it or gives you an error. Just try to copy some files to it.

edit: you beat me to it :D you don't need sudo to read the usb. In fact it will only output the usb info AFAIK.

---

