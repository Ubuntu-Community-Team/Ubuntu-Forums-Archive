---
title: "NIC not working after Airodump used"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by andytof47 on 2007-01-17
hi I'm using a wusb54g and fired up airodump it reads my network fine but after i put airodump to sleep - e.g quit it 

I put my nic down with

sudo ifconfig rausb0 down

then up again

sudo ifconfig rausb0 up

and this usually brings it back to a default 

but not now  pleeeeeeeaaaaaasssseeeeee help

I can't ping, can't anything

---

### Post by zgornel on 2007-01-17
Type "iwconfig" and check that the card is in the "Managed" mode.

---

### Post by andytof47 on 2007-01-17
OK all is cool now 

Cheers:KS

---

