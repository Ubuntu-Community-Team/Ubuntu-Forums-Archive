---
title: "Atheros chipset version in MacBook Core Duo"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-06
Anyone know the Atheros chipset version in the first-gen MacBooks?  (not Pro or C2D)

```

ben@macbook:~$ sudo lspci -vv

```
gives this for the atheros wireless adapter:
```

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
	Subsystem: Apple Computer Inc. Unknown device 0086
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <512ns, L1 <64us
		Link: ASPM L0s L1 Enabled RCB 128 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000

```

notice :  Unknown device 001c (rev 01)
where the chipset version should be.  Anyone know what it is?

---

### Post by ronocdh on 2007-05-07
If **lspci** yields an unknown, do **sudo update-pciids** then run it again.

---

### Post by benanzo on 2007-05-07
sweet.  that fixed it.

```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

---

### Post by ferarg on 2007-05-30
Hi, I have the same problem, ubuntu feisty dont recognized the Atheros interface, but with he command "sudo update-pciids" did it.

now, how can I "connect" that "new device" with an interface to use it like a wlan interface.

thanks

---

### Post by ronocdh on 2007-05-30
> **ferarg said:**
> Hi, I have the same problem, ubuntu feisty dont recognized the Atheros interface, but with he command "sudo update-pciids" did it.

now, how can I "connect" that "new device" with an interface to use it like a wlan interface.

thanks
I'm not sure I understand your question, but you're saying you want your wireless card to work, right? Try [this tutorial]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") on Madwifi. If that totally steers you wrong, you can always try ndiswrapper, but the former is open source, so I must recommend it first!

---

### Post by reckless2k2 on 2007-05-30
is this a mac only issue since i remember there being atheros modules in the kernel for those chipsets? 

Are you saying that atheros chipsets are not native in ubuntu anymore? I had my atheros working out of box in 5.04 thru 6.10.

---

### Post by ronocdh on 2007-05-30
> **reckless2k2 said:**
> is this a mac only issue since i remember there being atheros modules in the kernel for those chipsets? 

Are you saying that atheros chipsets are not native in ubuntu anymore? I had my atheros working out of box in 5.04 thru 6.10.
I'd be interested to hear more about your hardware setup (full computer, as well as the exact Atheros you had). It was my understanding that the Atheros chipsets were closed, and the Madwifi guys were valiantly blackboxing them. This was why the wireless reception is never better than 80% what can be gotten in OS X. =/ But hey, it's open source!

Someone please post if I'm mistaken... perhaps it's just the specific chipsets which are found in the Mactels?

---

### Post by reckless2k2 on 2007-05-30
Yeah well i was using IBM T42 for a few years and madwifi was native so I didn't have to bug with it. it just worked. Then suse required that i patch myself. i remember at the end with ubuntu a version or 2 ago that i had issues with madwifi not working so good as a previous distro version. I'm not sure. I just thought atheros was builtin to ubuntu definitely. i guess i'm wrong. i thought everyone is supposed to be working towards getting wifi working well in linux. haha. atheros was native for so long and now it's in nothing? ugh. the big plus with atheros in pentration testing distros was that it could inject and sniff. atheros was the card to have. hhmm.

---

### Post by ivesjd on 2007-06-02
Ive got the same chipset as Benanzo and am experiencing drops of my connection. Then every few drops it fails to reconnect and I have to either restart network manager or reboot.
 
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

I compiled madwifi from source (version 9.3.1 i belive) which helped with the signal strength. I now get 70-80% instead of 50%. But I am still getting the drops. Any Ideas?

---

### Post by ivesjd on 2007-06-02
I think I may have fixed it, I went with Knetwork manager and it seems to be working better. Ill let you know after a few days once I can really test it out. 

***edit***
One thing I forgot to mention, it only seemed to drop in my apartment. Which has an older wireless b router (no access to it). When I was on campus with a wireless g router, it worked fine. Hopefully with Knetwork manager Ill be good in both places.
***/edit***

---

### Post by ivesjd on 2007-06-04
Its been over 24hours now using Knetwork Manager, and I haven't had any drops. It is strange that Knetwork Manager works so much better then the default gnome network manager. But it did for me. Thats with recompiled madwifi on first gen macbook.

---

