---
title: "[SOLVED] Strange internet problem!  Please help"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-03-27
I have an XP-dapper dual boot machine.  Last night, I loaded into Ubuntu as usual and couldnt connect to the web - got a message in Firefox saying I had been disconnected and GAIM wouldnt work either.  So I booted into Windows XP and there was nothing wrong with the internet (so I know its not my broadband box).  I booted back into Ubuntu and it was then working perfectly ok so I stayed on it all night with no problems.  So thinking it was a freak occurance, I paid it no attention.  However, tonight, the same thing has happened except Ive tried booting into Ubuntu twice and this time it hasnt come back.  I have two log-ons for ubuntu, both administrator log-ins and I tried my second login just in case id broke my main one somehow - no different.  (I havent used the back up login for weeks).  

I use an orange livebox broadband modem connected by ethernet if that helps (to my motherboard) and I have all the correct lights etc (well im using it now through xp so it must work).  

Does anyone have any ideas what this may be and how to fix it?  I was working before and I havent done any upgrading or installed anything to my knowledge that would have an effect - only the usual system updates.  I was messing about with Joomla for my website but im assured that this wouldnt have made a difference.

Please help!

---

### Post by Iarwain ben-adar on 2007-03-27
Hi,

if you have dhcp (a dynamic ip-address) try this:
```
sudo dhclient
```

Or if you have a static, 
```
sudo etc/init.d/networking restart
```

Don't really know if the latter works (it just restart all you networking, might give you an error to troubleshoot)


Iarwain

---

### Post by octoberdan on 2007-03-27
After trying that, could you please open up a console, enter "ifconfig" and then report back with the results?

---

### Post by MikeSz on 2007-03-27
sure, give me five mins to re-boot etc...

---

### Post by MikeSz on 2007-03-27
Ok, this is a little strange.  Ive booted into Ubuntu and the internet has worked straight away.  Is this a rogue broadband connection do you think (havent had any problems with windows XP though :confused:  )

Do you still want the results of those commands by the way guys?

Cheers,
Mike

---

### Post by camz on 2007-03-27
try "dhclient (item name e.g wlan0, rausb0)"

so for me, it's dhclient rausb0

---

### Post by camz on 2007-03-27
Sorry, posted that before you posted that last one..

---

### Post by octoberdan on 2007-03-27
> **MikeSz said:**
> Ok, this is a little strange.  Ive booted into Ubuntu and the internet has worked straight away.  Is this a rogue broadband connection do you think (havent had any problems with windows XP though :confused:  )

Do you still want the results of those commands by the way guys?

Cheers,
Mike

At this point you might want to head over to [http://help.orange.co.uk/categoryBrowse.do](http://help.orange.co.uk/categoryBrowse.do)

---

### Post by MikeSz on 2007-03-27
ok, thanks a lot guys I really appreciate all the help :)  Ive run the commands suggested just for info and pasted it below.  Wasnt quite sure about the dhclient command, so I just guessed it meant eth0 as thats what came up from the previous command :confused:   anyway, here it is.....

bespin@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:F2:D7:8F
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fef2:d78f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:790944 (772.4 KiB)  TX bytes:192533 (188.0 KiB)
          Interrupt:217 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

bespin@mike-desktop:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
bespin@mike-desktop:~$

---

### Post by Iarwain ben-adar on 2007-03-27
For the dhclient command, you have to put sudo in front of it
=> sudo dhclient eth0


Iarwain

---

### Post by jerryrw on 2007-03-27
add a 'sudo' to that 'dhclient eth0' and post that

---

### Post by MikeSz on 2007-03-27
Cheers for the link Octoberdan, I thought it may be an orange problem at first, but ive been down in linux tonight for about an hour and all the time ive been switching back and forth between ubuntu and XP and although ubuntu hasnt been working online, XP has.  Thats whats been confusing me and made me think it was nothing to do with orange or my hardware, cos as soon as I restarted into XP, it all worked without any problems - switch back to ubuntu and it was down again.  :confused:

---

### Post by MikeSz on 2007-03-27
sorry, im running behind here - he'res the output

bespin@mike-desktop:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   LPF/eth0/00:0f:ea:f2:d7:8f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.90 -- renewal in 41368 seconds.
bespin@mike-desktop:~$

---

### Post by MikeSz on 2007-03-27
does that help?

---

### Post by Iarwain ben-adar on 2007-03-27
Well, it does not give any error :D

Just a stupid question: are you sure your cables are insterted good? (not loose)

I had a similar problem some time ago, so you could try that..


Iarwain

---

### Post by MikeSz on 2007-03-27
No such thing as a stupid question here, lol.  Yeah, it was the first thing I checked to be honest.  I thought it might be a dicky cable as ive just had to replace an extension lead so thought it might be that.

---

### Post by Iarwain ben-adar on 2007-03-27
So,  something for you to do :D :

cat /var/log/messages
OR
cat /var/log/messages.0

(see the date on those lines, so that the date matches the date that the pc did weird)

See if there are some errors somewhere with networking or such.

Sorry to give such a vague tip,
but i don't know how to explain it otherwise :D

Or you could just post the whole thing here, and we'll try to look into it xD


Iarwain

---

### Post by Ajex on 2007-03-27
I think i have a similar problem if not the same one. 
Lastnight my internet for this machine was working fine, but this morning I had some trouble getting on to the net.
 So i jumped back and forth between XP and Ubuntu trying different things, im new to all of this so i don't know much about it, (so i tryed a little bit of XP style fixing).
 To get my internet working again i just went in to System > Administration > Networking and stopped my eth0 connection and then re-enabled it... it works fine now, but only untill i restart. I'm not sure if that can shed some light on the issue, but at least it could be a short term fix. 
Hope this helps, If only for a short while. :)

---

### Post by MikeSz on 2007-03-27
think it may be a bit large but here goes...

CA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.232000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.236000] Linux Plug and Play Suppo rt v0.97 (c) Adam Belay
Mar 27 17:25:03 mike-desktop kernel: [17179570.236000] pnp: PnP ACPI init
Mar 27 17:25:03 mike-desktop kernel: [17179570.240000] pnp: PnP ACPI: found 12 d evices
Mar 27 17:25:03 mike-desktop kernel: [17179570.240000] PnPBIOS: Disabled by ACPI  PNP
Mar 27 17:25:03 mike-desktop kernel: [17179570.240000] PCI: Using ACPI for IRQ r outing
Mar 27 17:25:03 mike-desktop kernel: [17179570.240000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] PCI: Bridge: 0000:00:09.0
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   IO window: 9000-9fff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   MEM window: disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   PREFETCH window: disabl ed.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] PCI: Bridge: 0000:00:0b.0
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   IO window: 8000-8fff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   MEM window: disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   PREFETCH window: disabl ed.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] PCI: Bridge: 0000:00:0c.0
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   IO window: 7000-7fff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   MEM window: disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   PREFETCH window: disabl ed.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] PCI: Bridge: 0000:00:0d.0
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   IO window: 6000-6fff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   MEM window: disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   PREFETCH window: disabl ed.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] PCI: Bridge: 0000:00:0e.0
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   IO window: disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   MEM window: f0000000-f7 ffffff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000]   PREFETCH window: e00000 00-efffffff
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] audit: initializing netli nk socket (disabled)
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] audit(1175016275.268:1): initialized
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] highmem bounce pool size:  64 pages
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] VFS: Disk quotas dquot_6. 5.1
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] Dquot-cache hash table en tries: 1024 (order 0, 4096 bytes)
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] Initializing Cryptographi c API
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] io scheduler noop registe red
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] io scheduler anticipatory  registered
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] io scheduler deadline reg istered
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] io scheduler cfq register ed
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pcie_portdrv_probe->Dev[0 05d:10de] has invalid IRQ. Check vendor BIOS
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] assign_interrupt_mode Fou nd MSI capability
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pcie_portdrv_probe->Dev[0 05d:10de] has invalid IRQ. Check vendor BIOS
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] assign_interrupt_mode Fou nd MSI capability
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pcie_portdrv_probe->Dev[0 05d:10de] has invalid IRQ. Check vendor BIOS
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] assign_interrupt_mode Fou nd MSI capability
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] pcie_portdrv_probe->Dev[0 05d:10de] has invalid IRQ. Check vendor BIOS
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] assign_interrupt_mode Fou nd MSI capability
Mar 27 17:25:03 mike-desktop kernel: [17179570.268000] isapnp: Scanning for PnP cards...
Mar 27 17:25:03 mike-desktop kernel: [17179570.620000] isapnp: No Plug & Play de vice found
Mar 27 17:25:03 mike-desktop kernel: [17179570.632000] PNP: No PS/2 controller f ound. Probing ports directly.
Mar 27 17:25:03 mike-desktop kernel: [17179571.160000] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Serial: 8250/16550 driver  $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] 00:07: ttyS0 at I/O 0x3f8  (irq = 4) is a 16550A
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] 00:08: ttyS1 at I/O 0x2f8  (irq = 3) is a 16550A
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] RAMDISK driver initialize d: 16 RAM disks of 65536K size 1024 blocksize
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Uniform Multi-Platform E- IDE driver Revision: 7.00alpha2
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] ide: Assuming 33MHz syste m bus speed for PIO modes; override with idebus=xx
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] mice: PS/2 mouse device c ommon for all mice
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] EISA: Probing bus 0 at ei sa.0
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Cannot allocate resource for EISA slot 1
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Cannot allocate resource for EISA slot 6
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Cannot allocate resource for EISA slot 7
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] Cannot allocate resource for EISA slot 8
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] EISA: Detected 0 cards.
Mar 27 17:25:03 mike-desktop kernel: [17179571.168000] NET: Registered protocol family 2
Mar 27 17:25:03 mike-desktop kernel: [17179571.816000] input: AT Translated Set 2 keyboard as /class/input/input0
Mar 27 17:25:03 mike-desktop kernel: [17179571.816000] IP route cache hash table  entries: 65536 (order: 6, 262144 bytes)
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] TCP established hash tabl e entries: 262144 (order: 8, 1048576 bytes)
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] TCP bind hash table entri es: 65536 (order: 6, 262144 bytes)
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] TCP: Hash tables configur ed (established 262144 bind 65536)
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] TCP reno registered
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] TCP bic registered
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] NET: Registered protocol family 1
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] NET: Registered protocol family 8
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] NET: Registered protocol family 20
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] Using IPI Shortcut mode
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] ACPI wakeup devices:
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] ACPI: (supports S0 S1 S4 S5)
Mar 27 17:25:03 mike-desktop kernel: [17179571.820000] Freeing unused kernel mem ory: 288k freed
Mar 27 17:25:03 mike-desktop kernel: [17179571.856000] vga16fb: mapped to 0xc00a 0000
Mar 27 17:25:03 mike-desktop kernel: [17179572.044000] Console: switching to col our frame buffer device 80x25
Mar 27 17:25:03 mike-desktop kernel: [17179572.044000] fb0: VGA16 VGA frame buff er device
Mar 27 17:25:03 mike-desktop kernel: [17179573.060000] Capability LSM initialize d
Mar 27 17:25:03 mike-desktop kernel: [17179573.208000] ACPI: Processor [CPU0] (s upports 8 throttling states)
Mar 27 17:25:03 mike-desktop kernel: [17179573.624000] SCSI subsystem initialize d
Mar 27 17:25:03 mike-desktop kernel: [17179573.624000] ACPI: bus type scsi regis tered
Mar 27 17:25:03 mike-desktop kernel: [17179573.628000] **** SET: Misaligned reso urce pointer: df8c9a02 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179573.628000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Mar 27 17:25:03 mike-desktop kernel: [17179573.628000] ACPI: PCI Interrupt 0000: 00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 217
Mar 27 17:25:03 mike-desktop kernel: [17179573.628000] ata1: SATA max UDMA/133 c md 0x9F0 ctl 0xBF2 bmdma 0xCC00 irq 217
Mar 27 17:25:03 mike-desktop kernel: [17179573.628000] ata2: SATA max UDMA/133 c md 0x970 ctl 0xB72 bmdma 0xCC08 irq 217
Mar 27 17:25:03 mike-desktop kernel: [17179573.832000] ata1: no device found (ph y stat 00000000)
Mar 27 17:25:03 mike-desktop kernel: [17179573.832000] scsi0 : sata_nv
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] ata2: no device found (ph y stat 00000000)
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] scsi1 : sata_nv
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] **** SET: Misaligned reso urce pointer: df8c9902 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] ACPI: PCI Interrupt 0000: 00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 225
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] ata3: SATA max UDMA/133 c md 0x9E0 ctl 0xBE2 bmdma 0xE000 irq 225
Mar 27 17:25:03 mike-desktop kernel: [17179574.036000] ata4: SATA max UDMA/133 c md 0x960 ctl 0xB62 bmdma 0xE008 irq 225
Mar 27 17:25:03 mike-desktop kernel: [17179574.240000] ata3: no device found (ph y stat 00000000)
Mar 27 17:25:03 mike-desktop kernel: [17179574.240000] scsi2 : sata_nv
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] ata4: no device found (ph y stat 00000000)
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] scsi3 : sata_nv
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] NFORCE-CK804: IDE control ler at PCI slot 0000:00:06.0
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] NFORCE-CK804: chipset rev ision 162
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] NFORCE-CK804: not 100%% n ative mode: will probe irqs later
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000] NFORCE-CK804: 0000:00:06. 0 (rev a2) UDMA133 controller
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000]     ide0: BM-DMA at 0xf00 0-0xf007, BIOS settings: hda:DMA, hdb:DMA
Mar 27 17:25:03 mike-desktop kernel: [17179574.444000]     ide1: BM-DMA at 0xf00 8-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Mar 27 17:25:03 mike-desktop kernel: [17179574.732000] hda: Maxtor 6Y080P0, ATA DISK drive
Mar 27 17:25:03 mike-desktop kernel: [17179575.012000] hdb: IC35L120AVVA07-0, AT A DISK drive
Mar 27 17:25:03 mike-desktop kernel: [17179575.068000] ide0 at 0x1f0-0x1f7,0x3f6  on irq 14
Mar 27 17:25:03 mike-desktop kernel: [17179575.824000] hdc: PIONEER DVD RW DVR-1 06D, ATAPI CD/DVD-ROM drive
Mar 27 17:25:03 mike-desktop kernel: [17179576.608000] hdd: PIONEER DVD-RW DVR-1 03, ATAPI CD/DVD-ROM drive
Mar 27 17:25:03 mike-desktop kernel: [17179576.664000] ide1 at 0x170-0x177,0x376  on irq 15
Mar 27 17:25:03 mike-desktop kernel: [17179576.672000] hda: max request size: 12 8KiB
Mar 27 17:25:03 mike-desktop kernel: [17179576.684000] hda: Host Protected Area detected.
Mar 27 17:25:03 mike-desktop kernel: [17179576.684000] ^Icurrent capacity is 160 084415 sectors (81963 MB)
Mar 27 17:25:03 mike-desktop kernel: [17179576.684000] ^Inative  capacity is 160 086528 sectors (81964 MB)
Mar 27 17:25:03 mike-desktop kernel: [17179576.700000] hda: Host Protected Area disabled.
Mar 27 17:25:03 mike-desktop kernel: [17179576.700000] hda: 160086528 sectors (8 1964 MB) w/7936KiB Cache, CHS=65535/16/63, UDMA(133)
Mar 27 17:25:03 mike-desktop kernel: [17179576.700000] hda: cache flushes suppor ted
Mar 27 17:25:03 mike-desktop kernel: [17179576.700000]  hda: hda1 hda2 < hda5 hd a6 > hda3
Mar 27 17:25:03 mike-desktop kernel: [17179576.748000] hdb: max request size: 12 8KiB
Mar 27 17:25:03 mike-desktop kernel: [17179576.748000] hdb: 241254720 sectors (1 23522 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
Mar 27 17:25:03 mike-desktop kernel: [17179576.748000] hdb: cache flushes suppor ted
Mar 27 17:25:03 mike-desktop kernel: [17179576.748000]  hdb: hdb1
Mar 27 17:25:03 mike-desktop kernel: [17179576.756000] hdc: ATAPI 63X DVD-ROM DV D-R CD-R/RW drive, 2000kB Cache, UDMA(33)
Mar 27 17:25:03 mike-desktop kernel: [17179576.756000] Uniform CD-ROM driver Rev ision: 3.20
Mar 27 17:25:03 mike-desktop kernel: [17179576.792000] hdd: ATAPI 24X DVD-ROM DV D-R CD-R/RW drive, 2000kB Cache, DMA
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] usbcore: registered new d river usbfs
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] usbcore: registered new d river hub
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] **** SET: Misaligned reso urce pointer: dfa4a5c2 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] ACPI: PCI Interrupt 0000: 00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 233
Mar 27 17:25:03 mike-desktop kernel: [17179577.136000] ohci_hcd 0000:00:02.0: OH CI Host Controller
Mar 27 17:25:03 mike-desktop kernel: [17179577.152000] ohci_hcd 0000:00:02.0: ne w USB bus registered, assigned bus number 1
Mar 27 17:25:03 mike-desktop kernel: [17179577.152000] ohci_hcd 0000:00:02.0: ir q 233, io mem 0xf8005000
Mar 27 17:25:03 mike-desktop kernel: [17179577.208000] hub 1-0:1.0: USB hub foun d
Mar 27 17:25:03 mike-desktop kernel: [17179577.208000] hub 1-0:1.0: 10 ports det ected
Mar 27 17:25:03 mike-desktop kernel: [17179577.212000] forcedeth.c: Reverse Engi neered nForce ethernet driver. Version 0.54.
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] **** SET: Misaligned reso urce pointer: dfa4a2c2 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ACPI: PCI Interrupt 0000: 00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 50
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ehci_hcd 0000:00:02.1: EH CI Host Controller
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ehci_hcd 0000:00:02.1: de bug port 1
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ehci_hcd 0000:00:02.1: ne w USB bus registered, assigned bus number 2
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ehci_hcd 0000:00:02.1: ir q 50, io mem 0xf8006000
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] ehci_hcd 0000:00:02.1: US B 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] hub 2-0:1.0: USB hub foun d
Mar 27 17:25:03 mike-desktop kernel: [17179577.312000] hub 2-0:1.0: 10 ports det ected
Mar 27 17:25:03 mike-desktop kernel: [17179577.416000] **** SET: Misaligned reso urce pointer: dfa5af02 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179577.416000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Mar 27 17:25:03 mike-desktop kernel: [17179577.416000] ACPI: PCI Interrupt 0000: 00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 217
Mar 27 17:25:03 mike-desktop kernel: [17179577.416000] forcedeth: using HIGHDMA
Mar 27 17:25:03 mike-desktop kernel: [17179577.936000] eth0: forcedeth.c: subsys tem: 01458:e000 bound to 0000:00:0a.0
Mar 27 17:25:03 mike-desktop kernel: [17179577.992000] Attempting manual resume
Mar 27 17:25:03 mike-desktop kernel: [17179578.008000] kjournald starting.  Comm it interval 5 seconds
Mar 27 17:25:03 mike-desktop kernel: [17179578.008000] EXT3-fs: mounted filesyst em with ordered data mode.
Mar 27 17:25:03 mike-desktop kernel: [17179578.272000] usb 1-7: new low speed US B device using ohci_hcd and address 2
Mar 27 17:25:03 mike-desktop kernel: [17179578.784000] usb 1-8: new low speed US B device using ohci_hcd and address 3
Mar 27 17:25:03 mike-desktop kernel: [17179586.176000] i2c_adapter i2c-0: nForce 2 SMBus adapter at 0x1c00
Mar 27 17:25:03 mike-desktop kernel: [17179586.176000] i2c_adapter i2c-1: nForce 2 SMBus adapter at 0x1c40
Mar 27 17:25:03 mike-desktop kernel: [17179586.516000] pci_hotplug: PCI Hot Plug  PCI Core version: 0.5
Mar 27 17:25:03 mike-desktop kernel: [17179586.520000] shpchp: Standard Hot Plug  PCI Controller Driver version: 0.4
Mar 27 17:25:03 mike-desktop kernel: [17179586.612000] **** SET: Misaligned reso urce pointer: f7e41bc2 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179586.612000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Mar 27 17:25:03 mike-desktop kernel: [17179586.612000] ACPI: PCI Interrupt 0000: 00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 225
Mar 27 17:25:03 mike-desktop kernel: [17179586.680000] input: PC Speaker as /cla ss/input/input1
Mar 27 17:25:03 mike-desktop kernel: [17179586.700000] Real Time Clock Driver v1 .12
Mar 27 17:25:03 mike-desktop kernel: [17179586.708000] NET: Registered protocol family 17
Mar 27 17:25:03 mike-desktop kernel: [17179586.708000] parport: PnPBIOS parport detected.
Mar 27 17:25:03 mike-desktop kernel: [17179586.708000] parport0: PC-style at 0x3 78, irq 7 [PCSPP,TRISTATE]
Mar 27 17:25:03 mike-desktop kernel: [17179586.732000] parport0: Printer, HEWLET T-PACKARD DESKJET 820C
Mar 27 17:25:03 mike-desktop kernel: [17179586.752000] Floppy drive(s): fd0 is 1 .44M
Mar 27 17:25:03 mike-desktop kernel: [17179586.808000] FDC 0 is a post-1991 8207 7
Mar 27 17:25:03 mike-desktop kernel: [17179586.932000] intel8x0_measure_ac97_clo ck: measured 54658 usecs
Mar 27 17:25:03 mike-desktop kernel: [17179586.932000] intel8x0: clocking to 469 89
Mar 27 17:25:03 mike-desktop kernel: [17179587.012000] Linux agpgart interface v 0.101 (c) Dave Jones
Mar 27 17:25:03 mike-desktop kernel: [17179587.012000] usbcore: registered new d river hiddev
Mar 27 17:25:03 mike-desktop kernel: [17179587.024000] input: HID 046a:0023 as / class/input/input2
Mar 27 17:25:03 mike-desktop kernel: [17179587.024000] input: USB HID v1.11 Keyb oard [HID 046a:0023] on usb-0000:00:02.0-7
Mar 27 17:25:03 mike-desktop kernel: [17179587.040000] input: HID 046a:0023 as / class/input/input3
Mar 27 17:25:03 mike-desktop kernel: [17179587.040000] input: USB HID v1.11 Devi ce [HID 046a:0023] on usb-0000:00:02.0-7
Mar 27 17:25:03 mike-desktop kernel: [17179587.048000] input: HID 062a:0000 as / class/input/input4
Mar 27 17:25:03 mike-desktop kernel: [17179587.048000] input: USB HID v1.10 Mous e [HID 062a:0000] on usb-0000:00:02.0-8
Mar 27 17:25:03 mike-desktop kernel: [17179587.048000] usbcore: registered new d river usbhid
Mar 27 17:25:03 mike-desktop kernel: [17179587.048000] drivers/usb/input/hid-cor e.c: v2.6:USB HID core driver
Mar 27 17:25:03 mike-desktop kernel: [17179587.344000] ts: Compaq touchscreen pr otocol output
Mar 27 17:25:03 mike-desktop kernel: [17179587.368000] nvidia: module license 'N VIDIA' taints kernel.
Mar 27 17:25:03 mike-desktop kernel: [17179587.372000] **** SET: Misaligned reso urce pointer: f7dfc0c2 Type 07 Len 0
Mar 27 17:25:03 mike-desktop kernel: [17179587.372000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Mar 27 17:25:03 mike-desktop kernel: [17179587.372000] ACPI: PCI Interrupt 0000: 05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 58
Mar 27 17:25:03 mike-desktop kernel: [17179587.372000] NVRM: loading NVIDIA Linu x x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Mar 27 17:25:03 mike-desktop kernel: [17179587.480000] NET: Registered protocol family 10
Mar 27 17:25:03 mike-desktop kernel: [17179587.480000] lo: Disabled Privacy Exte nsions
Mar 27 17:25:03 mike-desktop kernel: [17179587.480000] IPv6 over IPv4 tunneling driver
Mar 27 17:25:03 mike-desktop kernel: [17179588.740000] lp0: using parport0 (inte rrupt-driven).
Mar 27 17:25:03 mike-desktop kernel: [17179588.776000] Adding 1453840k swap on / dev/hda6.  Priority:-1 extents:1 across:1453840k
Mar 27 17:25:03 mike-desktop kernel: [17179588.924000] EXT3 FS on hda3, internal  journal
Mar 27 17:25:03 mike-desktop kernel: [17179589.044000] md: md driver 0.90.3 MAX_ MD_DEVS=256, MD_SB_DISKS=27
Mar 27 17:25:03 mike-desktop kernel: [17179589.044000] md: bitmap version 4.39
Mar 27 17:25:03 mike-desktop kernel: [17179589.452000] device-mapper: 4.4.0-ioct l (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Mar 27 17:25:03 mike-desktop kernel: [17179589.984000] hdc: command error: statu s=0x51 { DriveReady SeekComplete Error }
Mar 27 17:25:03 mike-desktop kernel: [17179589.984000] hdc: command error: error =0x50 { LastFailedSense=0x05 }
Mar 27 17:25:03 mike-desktop kernel: [17179589.984000] ide: failed opcode was: u nknown
Mar 27 17:25:03 mike-desktop kernel: [17179589.984000] end_request: I/O error, d ev hdc, sector 14712448
Mar 27 17:25:03 mike-desktop kernel: [17179590.640000] cdrom: open failed.
Mar 27 17:25:03 mike-desktop kernel: [17179596.072000] ip_tables: (C) 2000-2002 Netfilter core team
Mar 27 17:25:03 mike-desktop kernel: [17179597.404000] ACPI: Power Button (FF) [ PWRF]
Mar 27 17:25:03 mike-desktop kernel: [17179597.404000] ACPI: Power Button (CM) [ PWRB]
Mar 27 17:25:03 mike-desktop kernel: [17179597.496000] pcc_acpi: loading...
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8:    0 : fid 0 x10 (2400 MHz), vid 0x2 (1500 mV)
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8:    1 : fid 0 xe (2200 MHz), vid 0x6 (1400 mV)
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8:    2 : fid 0 xc (2000 MHz), vid 0xa (1300 mV)
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8:    3 : fid 0 xa (1800 MHz), vid 0xe (1200 mV)
Mar 27 17:25:03 mike-desktop kernel: [17179597.940000] powernow-k8:    4 : fid 0 x2 (1000 MHz), vid 0x12 (1100 mV)
Mar 27 17:25:05 mike-desktop hpiod: 0.9.7 accepting connections at 59239...
Mar 27 17:25:06 mike-desktop kernel: [17179601.708000] ppdev: user-space paralle l port driver
Mar 27 17:25:06 mike-desktop kernel: [17179602.068000] apm: BIOS version 1.2 Fla gs 0x07 (Driver version 1.16ac)
Mar 27 17:25:06 mike-desktop kernel: [17179602.068000] apm: overridden by ACPI.
Mar 27 17:25:07 mike-desktop kernel: [17179602.588000] Bluetooth: Core ver 2.8
Mar 27 17:25:07 mike-desktop kernel: [17179602.588000] NET: Registered protocol family 31
Mar 27 17:25:07 mike-desktop kernel: [17179602.588000] Bluetooth: HCI device and  connection manager initialized
Mar 27 17:25:07 mike-desktop kernel: [17179602.588000] Bluetooth: HCI socket lay er initialized
Mar 27 17:25:07 mike-desktop kernel: [17179602.592000] Bluetooth: L2CAP ver 2.8
Mar 27 17:25:07 mike-desktop kernel: [17179602.592000] Bluetooth: L2CAP socket l ayer initialized
Mar 27 17:25:07 mike-desktop kernel: [17179602.604000] Bluetooth: RFCOMM socket layer initialized
Mar 27 17:25:07 mike-desktop kernel: [17179602.604000] Bluetooth: RFCOMM TTY lay er initialized
Mar 27 17:25:07 mike-desktop kernel: [17179602.604000] Bluetooth: RFCOMM ver 1.7
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): starting (version 2.14.0), pi d 5115 user 'bespin'
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): Resolved address "xml:readonl y:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at positio n 0
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): Resolved address "xml:readwri te:/home/bespin/.gconf" to a writable configuration source at position 1
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): Resolved address "xml:readonl y:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position  2
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): Resolved address "xml:readonl y:/var/lib/gconf/debian.defaults" to a read-only configuration source at positio n 3
Mar 27 17:25:35 mike-desktop gconfd (bespin-5115): Resolved address "xml:readonl y:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 27 17:25:39 mike-desktop gconfd (bespin-5115): Resolved address "xml:readwri te:/home/bespin/.gconf" to a writable configuration source at position 0
Mar 27 17:45:02 mike-desktop -- MARK --
Mar 27 18:05:03 mike-desktop -- MARK --
Mar 27 18:25:03 mike-desktop -- MARK --
Mar 27 18:45:03 mike-desktop -- MARK --
Mar 27 19:05:04 mike-desktop -- MARK --
Mar 27 19:25:04 mike-desktop -- MARK --
bespin@mike-desktop:~$ cat /var/log/messages

---

### Post by Iarwain ben-adar on 2007-03-27
I can't seem to find anything flakey :?
(but then again, i do not know that much)

But is this the log when you could not get any internet?


Iarwain

---

### Post by almacen on 2007-03-27
I have exactly the same problem....I have been on ubuntu for a few months, and this just started on saturday or sunday, I haven't installed anything new apart from usual ubuntu updates.
To make it work I also have to go to system-adminstration-networking and disable and enable my connection manually....
Any ideas what could be causing the problem?

---

### Post by MikeSz on 2007-03-27
erm - good point.  I dont think it is so but im not sure. anyway, it seems to be working now anyway so I know its nothing pemenant.  If it goes again, il copy the log to a text file and post it.  Hopefully then there may be an explanation.  

Thanks for all the help everyone -  its appreciated!

---

### Post by Iarwain ben-adar on 2007-03-27
Well,
if it doesn't work then,
try the dhclient command..

It could help ;)

(or the /etc/init.d/networking restart command)


Iarwain

---

### Post by MikeSz on 2007-03-27
Hey almacen - sorry, posted over you there :shock:   Thats kind of weird because thats when my problems started.  Is it possible there is an update thats causing a problem?

---

### Post by almacen on 2007-03-27
> **MikeSz said:**
> Hey almacen - sorry, posted over you there :shock:   Thats kind of weird because thats when my problems started.  Is it possible there is an update thats causing a problem?

I think there must be a problem with some sort of an update... there also seems to be a good few posts about "wireless network not working", etc in the past few days.

I think that must be the same problem we have....

Anyone expert got any ideas?

---

### Post by MikeSz on 2007-03-27
that would make sense if there are others having the same problem - anyone else have any ideas on what may be causing this?

---

### Post by almacen on 2007-03-27
We are probably better off starting a new thread with the right title, might help....

---

### Post by Mairi on 2007-03-27
Well, that sounds similiar to something that happened to me about a year ago, back on Breezy. I had three old computers, one for Windows XP, one for Linux, and an Imac all in one with Jaguar. One morning, I booted into Ubuntu and there was no internet. It worked fine on the other two. But nothing I did worked to get it up in Linux, including reinstalling Ubuntu, and then an install of Fedora Core 5. No Linux Internet for me.
    I posted on forum, posted the output of whatever commands I was told to use. No one could figure it out. Finally, I booted the Imac and wrote down the working network settings, went back to Ubuntu and changed it from DHCP to static and set it to that address. Worked.
     I have no idea if it would have kept on working for good, that computer threw a mechanical hissy and died a sad little death. This might help, might not, but I thought I'd share, just in case it would. Good luck!

---

### Post by locke.dragon on 2007-03-27
since it's dual-boot, wireless sometimes gets shut off on laptops after booting into windows (at least on mine it does).  all you need to do do fix the problem is...

1. boot back into windows
2. turn on wireless via fn + wireless (f2 on my box)
3. shut down windows
4. boot into ubuntu

this works every time on my machine.  hope that helps!

---

### Post by octoberdan on 2007-04-06
By the way, did you contact Orange's support? Just wondering what they had to say.

---

