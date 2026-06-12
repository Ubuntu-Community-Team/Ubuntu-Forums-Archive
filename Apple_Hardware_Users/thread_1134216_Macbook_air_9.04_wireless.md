---
title: "Macbook air 9.04 wireless?"
date: 2009-04-23
forum: Apple Hardware Users
---

### Post by flxfxp on 2009-04-23
Hello,

Short question: How do I get wireless working on 9.04 for the Macbook Air?

Thanks,

Dennis

---

### Post by flxfxp on 2009-04-23
Post scriptum: The method described in the 8.10 wiki entry does not work.

---

### Post by cyberdork33 on 2009-04-23
> **flxfxp said:**
> Post scriptum: The method described in the 8.10 wiki entry does not work.
Did you look in System > Administration > Hardware Drivers

---

### Post by flxfxp on 2009-04-24
Yes, it says the Broadcom STA wireless drive is activated and in use. However, it does not give a scan option to the network manager. In Network tools I only have my loopback and "Unknown Interface (pan0)".

Regards,

Dennis

---

### Post by cyberdork33 on 2009-04-24
> **flxfxp said:**
> Yes, it says the Broadcom STA wireless drive is activated and in use. However, it does not give a scan option to the network manager. 
Have you rebooted since then?

---

### Post by flxfxp on 2009-04-24
Ah, my mistake :)
However, it wont access any wireless networks. I tried WPA Personal and WEP 128 bit.

Regards,

Dennis

---

### Post by flxfxp on 2009-04-27
Anyone? I still can't connect to wireless networks.
I tried setting it up using a static address, but that didn't make a difference.

Help is very much appreciated.

Regards,

Dennis

---

### Post by maffix on 2009-04-28
First excuse for my bad English!
I have had the same problem like you. I think it's a bug, but I have solved it so.
Open Synaptic and search and install "b43-fwcutter", it worked for me!

Good luck!

---

### Post by __david on 2009-04-28
I got wifi working on a MBP by deactivating the driver and activating it again (then reboot). Maybe that works for you, too?

---

### Post by maffix on 2009-04-28
No, because when deactivating and after activating the "Driver hardware" tool it did not downloaded and extracted anything regarding broadcom's firmware.
Also rebooting did not work for me!

PS: I have installed Jaunty Jacalope 64bit on Macbook Pro 4,1 with the same wireless driver.

---

### Post by flxfxp on 2009-04-28
I installed "b43-fwcutter" and rebooted. Wireless works :D

Thanks,

Dennis

---

### Post by peakperformance on 2009-04-28
I also deactivated and activated the hardware driver, networking worked fine after reboot

---

### Post by cyberdork33 on 2009-04-28
> **maffix said:**
> No, because when deactivating and after activating the "Driver hardware" tool it did not downloaded and extracted anything regarding broadcom's firmware.
Also rebooting did not work for me!

PS: I have installed Jaunty Jacalope 64bit on Macbook Pro 4,1 with the same wireless driver.
the broadcom supplied driver does nto require separate firmware like b43 does.

---

