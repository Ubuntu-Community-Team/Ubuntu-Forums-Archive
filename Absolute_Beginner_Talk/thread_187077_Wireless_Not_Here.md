---
title: "Wireless Not Here"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-06-02
Hello,


I don't think the wireless card in my laptop is being recognised at all. In the Networking button it doesn't list it and when I did iwconfig in terminal it said there was no wireless.

Can someone help me please?

---

### Post by carlosqueso on 2006-06-02
What card do you have, and are you using ndiswrapper?   Also, post the output of lspci

---

### Post by Dr Von Bon Bon on 2006-06-03
Sorry, I'm not entirely sure what card I have. It's a built in one on the Dell Latitude X300.

How would I find out please?

```
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
0000:02:04.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
0000:02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)

```

That's what came up with lspci.

Thanks.

---

### Post by ????? on 2006-06-03
You're using broadcom. You can try [this instead of ndis](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by Dr Von Bon Bon on 2006-06-03
I got up to the point where it asks me to sudo apt-get install bcm43xx-fwcutter but terminal or synaptic cannot find this program.

This looks like it could be the answer so would someone please mind helping how to install this file please?

---

### Post by Dr Von Bon Bon on 2006-06-04
Can anyone help please?

---

