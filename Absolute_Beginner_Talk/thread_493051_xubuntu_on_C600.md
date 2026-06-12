---
title: "xubuntu on C600"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by KARx on 2007-07-05
i have installed xubuntu on a dell c600 is working fine except it does not see that there is a bulitin NIC card. the card is a 3com 3ccfe575ct i have looked for drivers on dell and 3com. any thoughts?

---

### Post by solar george on 2007-07-05
Which version, I have read that fiesty should work.

---

### Post by KARx on 2007-07-05
Version 7.04 desktop standard install. it sees the modem just fine.

---

### Post by solar george on 2007-07-05
Type ifconfig and post the results

---

### Post by KARx on 2007-07-06
here are the results:
 lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have been successful at adding a wireless D-link card. here are the results with that running
ath0      Link encap:Ethernet  HWaddr 00:11:95:3C:3B:38  
          inet addr:192.168.1.42  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe3c:3b38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2621 (2.5 KiB)  TX bytes:1832 (1.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-3C-3B-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3642 errors:0 dropped:0 overruns:0 frame:939
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:224933 (219.6 KiB)  TX bytes:4854 (4.7 KiB)
          Interrupt:11 

I have also been trying to get my video display to 1024x768 i have an ATI m4 and have found linux 7 drivers on dell but i'm not sure how to add them.
thanks

---

### Post by KARx on 2007-07-08
found my anwser to the resolution for 1024x768 on an ATI card.
[http://ubuntuforums.org/showthread.php?t=495280&highlight=1024+ati](http://ubuntuforums.org/showthread.php?t=495280&highlight=1024+ati)

i just need a solution for the nic card.

thanks

---

### Post by solar george on 2007-07-08
Post the results of lspci.

---

### Post by KARx on 2007-07-10
results of lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

thanks for all your help. I realy like this install so far.

---

### Post by solar george on 2007-07-10
Did you have the dlink card in when you ran lspci?

If you did can you remove it and rerun lspci and post the resutls of that.

---

### Post by KARx on 2007-07-11
yes I did have the d-link in here are the results without it.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

thanks

---

### Post by ugm6hr on 2007-07-11
Does the ethernet work in another OS / Windows?  Is there a BIOS control to turn it on/off?

The reason I ask - is that it doesn't appear in *lspci* output, which suggests it is turned off...

---

### Post by solar george on 2007-07-11
> Does the ethernet work in another OS / Windows? Is there a BIOS control to turn it on/off?

The reason I ask - is that it doesn't appear in lspci output, which suggests it is turned off...

What he said.

---

### Post by ScottyP on 2008-05-31
Just installed Hardy on my Dell Inspiron 8100. Same NIC. Same problem. Hardy has no clue I have a NIC. Anyone ever find a fix to this?

Thanks!

---

### Post by ugm6hr on 2008-06-01
@ScottyP:
> **ugm6hr said:**
> Does the ethernet work in another OS / Windows?  Is there a BIOS control to turn it on/off?

The reason I ask - is that it doesn't appear in *lspci* output, which suggests it is turned off...

Also - post lspci

---

### Post by ScottyP on 2008-06-01
So I fixed my problem. It had absolutely nothing to do with Hardy. The same problem would've happened regardless of the operating system because....

...I opened up my laptop to see that my Mini PCI card was halfway unplugged. DOH!

[How to check Mini PCI card on Dell Inspiron 8100]("http://support.dell.com/support/edocs/systems/ins8100/en/sm_en/remove.htm#1050760")

---

