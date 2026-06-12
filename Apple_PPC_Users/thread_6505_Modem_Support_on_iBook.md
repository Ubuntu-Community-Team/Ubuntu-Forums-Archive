---
title: "Modem Support on iBook"
date: 2004-11-29
forum: Apple PPC Users
---

### Post by Simon_me on 2004-11-29
Hi all, 

I've just installed Ubuntulinux on my iBook G4. That wireless extreme is not work is known, but as it looks there is also a problem with the modem. Ubuntu can't detect the modem itself. Does anyone has had the same problem and is there any solution to it? 

Regards

Simon

---

### Post by Viro on 2004-11-30
[QUOTE=Simon_me]Hi all, 

I've just installed Ubuntulinux on my iBook G4. That wireless extreme is not work is known, but as it looks there is also a problem with the modem. Ubuntu can't detect the modem itself. Does anyone has had the same problem and is there any solution to it? 

Regards

Simon[/QUOTE]
 You need to use the Linuxant drivers for the modem in the iBooks/Powerbooks. These are commercial closed sourced drivers, so you will have to pay for them.

---

### Post by Laf on 2005-01-04
Airport Extreme (last one, with Broadcom chipset) is not working on Linux and might never be. If i can give you an advice : you can sell it for about 70 euros and buy an USB wifi key for about 50 euros.

But not all USB wifi keys are working under Linux, you have to search for this.

Do "lspci" if you have a line like this one : "0001:01:12.0 Network controller: Broadcom Corporation BCM94306 802.11g (rev 03)" you can be sure that you won't be able to use it.

-

About Linuxant drivers... mine doesn't work, i can't install them... i'm still searching.

If you are lucky with compilation, please post some informations here.

---

### Post by tiiim on 2005-01-05
[QUOTE=Laf]Airport Extreme (last one, with Broadcom chipset) is not working on Linux and might never be. If i can give you an advice : you can sell it for about 70 euros and buy an USB wifi key for about 50 euros.

But not all USB wifi keys are working under Linux, you have to search for this.

Do "lspci" if you have a line like this one : "0001:01:12.0 Network controller: Broadcom Corporation BCM94306 802.11g (rev 03)" you can be sure that you won't be able to use it.

-

About Linuxant drivers... mine doesn't work, i can't install them... i'm still searching.

If you are lucky with compilation, please post some informations here.[/QUOTE]
 modem drives on macs are a bit hmmmm as mentioned they are closed drivers if your one of the few that have the different modem you'll be ok if not.... time to get a dchp router on broadband....

---

