---
title: "Mobile Connection"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-04-12
Hi All,

I have Nokia 3230 Mobile, I want to connect to my pc and download the images and videos into my system.

Is there any way in Ubuntu OS?

Regards,
Srikrishnan

---

### Post by Capricori on 2008-04-12
This depends...
Do you have a USB lead for the phone?
Can you use bluetooth on your computer?
Are the images and videos stored on a memory card (and if not, can they be?)

If the answer to any of the above is 'yes', then the answer to your question is most probably yes.

Capricori

---

### Post by srikrishnan on 2008-04-15
Hi,

I have connected my mobile to pc through USB cable.

I have memory card in my mobile, Also I have taken photos and videos in my mobile

Eventhough my mobile was not recognized by my Ubuntu OS.

Regards,
Srikrishnan

---

### Post by Capricori on 2008-04-15
Right, do you have some kind of card reader on your PC that could be used to read the card in your phone?

If not, try plugging your phone into the computer, with the USB cable, and then, open a terminal, and type 'dmesg | tail' (without the quotes). Post the output up here.

Regards,
Capricori

---

### Post by srikrishnan on 2008-04-15
Hi,

This is the detail:

srikrishnan@srikrishnan-desktop:~$ dmesg | tail
[   32.962466] Bluetooth: RFCOMM socket layer initialized
[   32.962567] Bluetooth: RFCOMM TTY layer initialized
[   32.962569] Bluetooth: RFCOMM ver 1.8
[  213.071239] eth0: link up.
[  213.072519] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  218.497337] eth0: link down.
[  220.137935] eth0: link up.
[  223.809387] eth0: no IPv6 routers present
[  240.514635] NET: Registered protocol family 24
[  241.091077] ip_tables: (C) 2000-2006 Netfilter Core Team
srikrishnan@srikrishnan-desktop:~$ 

Regards,
Srikrishnan

---

### Post by srikrishnan on 2008-04-15
Hi,

Sorry, the above pasted output is wrong, that was generated before connected my mobile to my pc

Below is the right one:

srikrishnan@srikrishnan-desktop:~$ dmesg | tail
[ 7165.931938] end_request: I/O error, dev fd0, sector 0
[ 7173.677141] usb 2-7: new full speed USB device using ohci_hcd and address 2
[ 7173.900844] usb 2-7: configuration #1 chosen from 1 choice
[ 7174.404587] cdc_acm 2-7:1.5: ttyACM0: USB ACM device
[ 7174.523822] usbcore: registered new interface driver cdc_acm
[ 7174.523900] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 7178.093333] end_request: I/O error, dev fd0, sector 0
[ 7178.093342] Buffer I/O error on device fd0, logical block 0
[ 7190.254987] end_request: I/O error, dev fd0, sector 0
[ 7190.254996] Buffer I/O error on device fd0, logical block 0
srikrishnan@srikrishnan-desktop:~$ 


Sorry for the inconvenience.

Thanks,
Srikrishnan

---

### Post by Capricori on 2008-04-15
Hmm, that's not telling me what I was hoping to see, so it might be a little more difficult than I expected.
One thing - it seems to think that your phone is a USB modem. I believe that type of phone can be used as a USB modem, is there a setting on the phone somewhere that would allow you to choose the connection type - between modem and removable storage?

 Regards,

Capricori

---

