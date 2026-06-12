---
title: "Fesity Fawn Herd 5 and better WPA support?"
date: 2007-03-09
forum: Apple PPC Users
---

### Post by kingkool68 on 2007-03-09
Hey Everybody, 
I took the Linux plunge about a week ago and at one point WPA support was working just fine.  Last night, out of the blue, it just stopped working and I couldn't connect to my network.  Does anyone know if WPA support for PPC computers is any better in Feisty Fawn herd 5?  I may make the plunge and upgrade if anyone has some positive feedback.  Why does Linux have to be so complicated?

---

### Post by ditsch on 2007-03-10
I am running Feisty since Herd 3 on my iBook G4 with Airport Extreme (WPA) and I am experiencing no problems so far.

---

### Post by octopuskevin on 2007-03-29
maybe im wrong here, but hasn't PPC support been discontinued with edgy?

---

### Post by Toehead on 2007-03-29
No, Edgy still supports the PPC Architecture. So does Feisty for that matter, its just been reclassified as "unofficial"

---

### Post by ssam on 2007-03-29
> **Toehead said:**
> No, Edgy still supports the PPC Architecture. So does Feisty for that matter, its just been reclassified as "unofficial"

And they hid the ISOs :-)

[http://cdimage.ubuntu.com/ports/](http://cdimage.ubuntu.com/ports/)

---

### Post by octopuskevin on 2007-03-29
haha yeh

well actually im using it now, after doing a bit of digging, strange that the iso's were hidden, and the torrent were not online..

from what i have gathered seems like it is left to the community to work on, however if that actually happens or not is up for debate... still though things still do *work*

i got wpa up and running with no problem with network manager. im using a zd1211 usb chip because the airport crapped out.

what i did have to do though was enter wpa_passphrase and use the psk hex output as the password, rather then the password... maybe that can help you out

input wpa_passphrase <ssid> <password> 
and use the psk output,...

- kevin

---

### Post by ditsch on 2007-03-30
Yes, this WPA hex issue is filed as a bug since Dapper: 

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/52922](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/52922)

I wonder if it will ever be fixed...

---

