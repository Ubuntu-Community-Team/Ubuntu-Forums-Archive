---
title: "digital camera not recognized?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by humppa666 on 2008-04-16
Hi!

I'm a complete beginner and tried to import some foto's and video from my new digital camera Fuji finepix 480. The first time I did it everything worked perfectly, this time (while trying to import the images I saw a message that my camera isn't recognized and later got a message:
PTP protocol error, data expected.
Anyone has good advice?

---

### Post by humppa666 on 2008-04-17
Maybe I should've added that when I plugged the USB-cable to my computer, it did recognize it at first, asked me if I want to import foto's, later I saw a text that camera is not recognized and the PTP Protocol error...

What is so weird about it, that I managed to do it a few days earlier without any problems, now I just get the same message ( haven't changed any settings in my camera either)

Anyone good advice?

---

### Post by philinux on 2008-04-17
You could try the Gthumb app. Applications>Graphics.

Ii always works for me.

---

### Post by timcredible on 2008-04-17
most cameras, and the 4 fujis I have, have 2 type of usb connections ( if forget the names of them and don't have any of my cameras around), if one of the types don't work, change the camera setting to the other, which should just come across as just a usb storage device.  3 of my 4 fujis are recognized just fine, the other one i have to set it to be just a storage device.  then use digikam to download/edit/manage your photos.  more info on digikam [here.]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=49&Itemid=57")

---

### Post by humppa666 on 2008-04-19
Thanks for the advice, but still no success. We tried gthumb, but got the same message. The camera manual does not mention anything about switching modes (PTP/regular), so am I crazy?

---

### Post by de_valentin on 2008-04-25
Since I upgraded to 8.04 I have the same problem, my camera (canon Ixus 900ti) is recognized I get the question if I would like to import foto's. If I click 'Import foto's' nothing happens.

Going straight to gthumb and asking to import photo's I get the following error message 

```
An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x3115). Make sure this device is connected to the computer.
```

And there it ends.

please help because with the same upgrade something happened to the cardreader.

---

### Post by Game Theory on 2008-05-03
Since I updated to Heron I can't upload pictures either.
Except my camera is not even being recognized by the computer...which never had happened again?
Any thoughts? 

Thanks !:KS

---

### Post by toni_uk on 2008-05-17
same problem here with my Canon Ixus 70

running dmesg I get the following:

> [  563.332000] end_request: I/O error, dev sdb, sector 60796
[  563.332000] printk: 24 messages suppressed.
[  563.332000] Buffer I/O error on device sdb1, logical block 60745
[  717.556000] usb 2-4: new high speed USB device using ehci_hcd and address 12
[  717.668000] usb 2-4: device descriptor read/64, error -71
[  717.884000] usb 2-4: device descriptor read/64, error -71
[  718.100000] usb 2-4: new high speed USB device using ehci_hcd and address 13
[  718.212000] usb 2-4: device descriptor read/64, error -71
[  718.428000] usb 2-4: device descriptor read/64, error -71
[  718.644000] usb 2-4: new high speed USB device using ehci_hcd and address 14
[  719.052000] usb 2-4: device not accepting address 14, error -71
[  719.164000] usb 2-4: new high speed USB device using ehci_hcd and address 15
[  719.572000] usb 2-4: device not accepting address 15, error -71
[  801.752000] usb 2-4: new high speed USB device using ehci_hcd and address 16
[  801.864000] usb 2-4: device descriptor read/64, error -71
[  802.080000] usb 2-4: device descriptor read/64, error -71
[  802.296000] usb 2-4: new high speed USB device using ehci_hcd and address 17
[  802.408000] usb 2-4: device descriptor read/64, error -71
[  802.624000] usb 2-4: device descriptor read/64, error -71
[  802.840000] usb 2-4: new high speed USB device using ehci_hcd and address 18
[  803.248000] usb 2-4: device not accepting address 18, error -71
[  803.360000] usb 2-4: new high speed USB device using ehci_hcd and address 19
[  803.768000] usb 2-4: device not accepting address 19, error -71


Anyone? Cheers!

---

### Post by StaceyRVC on 2008-05-17
I had the same issue with a canon rebel xt. I ended up finding a thread on here that suggested using Picasa to import the pics. I installed that connected the camera, set it up as the "drive". Finally I was able to upload my pics... I had approx 300 pics on the card and it took about 45 minutes through picasa. I am going to end up buying a card reader to make my life a bit easier. [http://ubuntuforums.org/showthread.php?t=276030&highlight=canon+rebel+drivers](http://ubuntuforums.org/showthread.php?t=276030&highlight=canon+rebel+drivers) yes I know its not a canon, but it may help...

---

### Post by toni_uk on 2008-05-17
> **StaceyRVC said:**
> I had the same issue with a canon rebel xt. I ended up finding a thread on here that suggested using Picasa to import the pics. I installed that connected the camera, set it up as the "drive". Finally I was able to upload my pics... I had approx 300 pics on the card and it took about 45 minutes through picasa. I am going to end up buying a card reader to make my life a bit easier. [http://ubuntuforums.org/showthread.php?t=276030&highlight=canon+rebel+drivers](http://ubuntuforums.org/showthread.php?t=276030&highlight=canon+rebel+drivers) yes I know its not a canon, but it may help...

Thanks Stacey, Picassa, didn't really like it on Windows. Might have to go with the USB Card reader.

I was just hoping to find out why my camera is not recognised at all. 'No Camera detected' on F-Spot.

---

### Post by toni_uk on 2008-05-17
Just wanted to add - connected the camera to my Fedora 9 laptop and it recognises it immediately. 

Bummer - Fedora 9 better than Ubuntu?!?

---

### Post by sneeks on 2008-05-17
its so much easier with a card reader,and you can pick them up for a £1 !!!

---

### Post by humppa666 on 2008-06-01
Thanks for messages. Like few people suggested here, I opted for a cardreader, and now my problems are over.

---

