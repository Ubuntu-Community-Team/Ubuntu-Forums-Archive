---
title: "Need help finding chipset"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-03-24
Hey, still struggling to get my inventel wireless adaptor to work. I'm trying to get hold of it's chipset (so I can find the right driver) but nothing's working. If I run 'lspci' I get:

clare@linuxubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

I don't think that helps.
I followed this link:
[http://christer.homeip.net/wordpress/?page_id=8](http://christer.homeip.net/wordpress/?page_id=8) 
but nothing's working for me here either. I've emailed inventel too but I think the word linux frightened them..
I'd really appreciate anyone's ideas - I'm determined not to go back to m$ :(

Edit: that link above might help any other noobs who are having a similar problem - I know I'm not the only one..

---

### Post by bionnaki on 2006-03-24
maybe
sudo lshw

---

### Post by clareb on 2006-03-24
Thanks for the tip, that doesn't seem to be giving me any more info either. It seems like ubuntu just can't 'talk' to the darn thing at all. I'm trying to find my chipset by googling, but I'd really appreciate it if anyone's got any more ideas.

---

### Post by mdmarmer on 2006-03-24
Tell us more about the device and maybe someone can help

I have heard of Inventel USB device UR054G -- is this it?

Is there a revision or version number for the device

Is there information on Inventel web site?

Mike

---

### Post by clareb on 2006-03-24
Yup! That's the one - I was beginning to think I was the only one who had one :) It's V1.1. Inventel's website is no use at all, I've emailed their support, but I've had no response. 

Thanks for lending a hand.

---

