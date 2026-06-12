---
title: "USB and FW card for pm 6400 ( old world )"
date: 2005-02-22
forum: Apple PPC Users
---

### Post by pbarthelemy on 2005-02-22
Hi,

I'd like to know if there is any supported USB and Firewire POI card that I can put in a powermac 6400/200 ?

I have tried installing Ubuntu on it, as I get mixed signals on whether old world macs are suported by ubuntu... is it ?

TIA,
--philippe

---

### Post by hndrcks on 2005-02-22
I put a generic PCI USB card in my G3 all-in-one and it found it fine in OS9 and Ubuntu.  I use BootX to get to Ubuntu, so the USB card came in very handy at the end of the install - I was able to copy the boot kernel and initrd to a usb memory stick and transfer them to the MacOS partition after restarting (HFS+ partition, so direct transfer during the install was dicey).

I would suggest testing the card in MacOS first - if it works there you are golden.

---

