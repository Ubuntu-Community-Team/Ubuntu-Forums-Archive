---
title: "Wireless and madwifi"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-04-28
Hello,

I would just like to start by saying thanks to the many helpful persons on the Ubuntu Forums. I am learning a TON (though i am still a complete newb)!

Okay, I am having problems getting my wireless card to work. I have already talked to alot of people. I have an Proxim orinoco 11/a/b/g with ATHEROS 5212 (i think thats the number) and have an AMD 64 3700+...anyway I found out that madwifi makes the driver i need for this card. But now it seems that this madwifi driver is already included in the Ubuntu package. Is this true?

If not, I didn't really want to do the 'Subversion'. I just want a snap-shot of the driver, if that is possible. Do i still need to 'compile' the driver code?

I have been reading alot of forums posts, the wiki, and the how-tos....i'm still lost though. Thanks for bearing with me.

Maria

---

### Post by Maria_Firewire on 2006-04-29
well, to answer my own question...apparently madwifi DOES come automatically with Ubuntu (64 bit anyway). I finally got the connection to work, though it took a while. Last Question: Do i need to do something to get Ubuntu to save these wireless settings or is it good to go from here on?

Thanks Again,
:D 
Maria

---

### Post by testube_babies on 2006-04-29
You should be good to go.  I have two atheros-based cards and Ubuntu deals with them just fine.

If it doesn't work correctly, you may want to experiment with the latest madwifi drivers as per this guide: [http://www.ubuntuforums.org/showthread.php?t=105437](http://www.ubuntuforums.org/showthread.php?t=105437)

---

### Post by BlastXng on 2006-05-03
[QUOTE=testube_babies]You should be good to go.  I have two atheros-based cards and Ubuntu deals with them just fine.

If it doesn't work correctly, you may want to experiment with the latest madwifi drivers as per this guide: [http://www.ubuntuforums.org/showthread.php?t=105437](http://www.ubuntuforums.org/showthread.php?t=105437)[/QUOTE]

I tried some of this along with downloading and installing KDE. Can finally get my Atheros card seen but it never connects to my access point and the iwconfig commands don't seem to work.  Here is the output from lspci:

--- lspci out---
@nc6k:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 0 3)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03 )
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Rad eon 9600 M10]
0000:02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay C ontroller
0000:02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay C ontroller
0000:02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx MultiMediaBay Accelerator
0000:02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay C ontroller
0000:02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Giga bit Ethernet (rev 03)
---lspci end----

Now I see that Ubuntu sees it, i get the card set for DHCP, enter the essid and Encryption key in Gnome Networking, but I can never get connected. I would really love this to work for dragging a cable around the house isn't fun.

Tia,

Blast

---

