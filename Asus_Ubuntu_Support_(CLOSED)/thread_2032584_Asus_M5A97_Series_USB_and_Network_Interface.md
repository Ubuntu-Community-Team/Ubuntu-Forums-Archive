---
title: "Asus M5A97 Series USB and Network Interface"
date: 2012-07-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by CH3CH2OH on 2012-07-24
tl;dr - Use BIOS revision 1102 for your M5A97 ([http://dlm3cdnet.asus.com/pub/ASUS/mb/SocketAM3+/M5A97/M5A97-ASUS-1102.zip](http://dlm3cdnet.asus.com/pub/ASUS/mb/SocketAM3+/M5A97/M5A97-ASUS-1102.zip)). 1208 Borks USB + ethernet

I tried to update the firmware for my Asus M5A97 motherboard this morning. I have a fairly finicky dual boot setup, and I thought the new firmware might afford some greater stability. However, I have found (at least in my hands) the most recent BIOS revision breaks the kernel's ability to load the USB and the Realtek LAN Controller. I have tested the BIOS revisions 1208 and 1102 thus far. 1102 works quite well with only minor flaws, but 1208 is totally toxic. Hope this helps if anyone is stuck. At least the BIOS is easy to flash on modern mobos. The Asus EZ Flash utility is actually pretty nice.

---

