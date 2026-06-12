---
title: "Wireless Network"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by mrfro1989 on 2007-12-06
I just installed Ubuntu 7.10 as a dual boot last night, and I can't get my wireless network to work.

I'm on a Compaq Presario 2200 and I'm using the built in wireless network card.
The blue light that comes on in windows when the card is on doesn't come up in Ubuntu.

Could someone help me getting this to work?
or does anyone know where I can get a driver for this?  I tried the Windows Wireless network wrapper thing, but it didn't do anything.

Thanks

---

### Post by wormser on 2007-12-06
It will help us if we what type of card it is.  Post the results of the following command.

```
lspci
```

---

### Post by mrfro1989 on 2007-12-06
lspci comes up with this:

02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by wormser on 2007-12-06
I have a BCM4309 and got mine running by enabling Restricted Drivers.  I am not an expert in hardware but this is how I got mine working.

System> Administration> Restricted Drivers Manager.  Under Firmware enable Broadcom 43xx chipset family.  The little wizard asked you where to get the file.  I downloaded the file from the location given.  

FYI, I did have a problem with the card hanging during the shutdown process so I removed it.  A few days l installed it again and have not had a problem yet.

---

