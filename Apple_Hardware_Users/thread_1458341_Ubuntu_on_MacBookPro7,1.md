---
title: "Ubuntu on MacBookPro7,1"
date: 2010-04-19
forum: Apple Hardware Users
---

### Post by pklat on 2010-04-19
Has anyone had any success installing ubuntu (lucid or other) on the new 13'' MacbookPro7,1 ?

I've installed rEFIt after which both live and alternate lucid CDs start booting but soon stop as they "can't find a CD-ROM drive/driver".

Arch seems to give a similar error. Fedora 12 hangs in boot up due to what seems to be a graphics issue.

Any ideas?

---

### Post by jaco223 on 2010-04-19
> **pklat said:**
> Has anyone had any success installing ubuntu (lucid or other) on the new 13'' MacbookPro7,1 ?

I've installed rEFIt after which both live and alternate lucid CDs start booting but soon stop as they "can't find a CD-ROM drive/driver".

Arch seems to give a similar error. Fedora 12 hangs in boot up due to what seems to be a graphics issue.

Any ideas?
Did you use Bootcamp to create a partition to install Ubuntu on?
If you want to install Ubuntu Lucid place the cd in the drive, power off your computer,
start it up while holding down the "c" key, it should boot to the install screen, where you
have the option of trying it without installing, or you can choose to install.
At this screen you can press the "f6" key and disbale acpi and choose nomodesest,
try these options and see if you can boot. It takes a couple of minutes to start a "live"
session which will boot up to the Ubuntu desktop.
Hope this helps.

Jaco

---

### Post by pklat on 2010-04-19
Thanks for the quick reply.

Yes, I have a BOOTCAMP FAT32 partition. The install screen boots up after holding the C key. Then I select acpi=off and nomodesest as you instructed. The boot up starts and hangs on the following screen:

```

Busy Box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu9) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) Unable to find a medium containing a live file system

```

---

### Post by pklat on 2010-04-20
I managed to boot into live lucid from a usb drive. Now in the install guide there is no hard drive to install to. Gparted also only finds the usb stick at /dev/sda1

---

### Post by jaco223 on 2010-04-20
> **pklat said:**
> Thanks for the quick reply.

Yes, I have a BOOTCAMP FAT32 partition. The install screen boots up after holding the C key. Then I select acpi=off and nomodesest as you instructed. The boot up starts and hangs on the following screen:

```

Busy Box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu9) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) Unable to find a medium containing a live file system

```

Maybe the problem is with the the ".iso" you have downloaded. Did you try
downloading a different image? Perhaps trying a daily build?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Try burning the image at a slow speed like 4x.

It could be that the image you downloaded is corrupt.

Hope this helps.

Jaco

---

### Post by jaco223 on 2010-04-20
May I ask why you're using Busy Box?
Can you uninstall Busy Box and try installing Ubuntu?

Jaco

---

### Post by binary10 on 2010-04-20
You'll always see the busybox message when initrd fails to find the root disk or some other issue with your devices. It gives you a limited command set to do some script debugging etc

---

### Post by Seq on 2010-04-20
@jaco223: Busybox is part of the initramfs.

@pklat: It sounds like the sata adapter is not recognized. Do you know what chipset is in this? You'll have to find out either from tech specs, or from within Mac OS X (About this Mac > System Information, if memory serves). I only have a mbp5,3 at my disposal, so I can't reproduce your problem, obviously.

Unfortunately, you're a very, very early adopter and likely one of the first to try Linux on this particular machine.

---

### Post by Seq on 2010-04-20
> **Seq said:**
> Unfortunately, you're a very, very early adopter and likely one of the first to try Linux on this particular machine.

Wow, a google search for "[macbookpro7,1 linux]("http://www.google.ca/search?q=macbookpro7%2C1+linux")" brings up this thread.

---

### Post by pklat on 2010-04-20
The only way I can start a live lucid environment is by booting from a CD and USB simultaneously. Apparently once it cannot find CD rom it looks for the USB. Live ubuntu environment works fine except for WiFi and recognising any of the SATA drives. I don't know what's new from previous versions of Macbook, but here is some info

```

Hardware Overview:

  Model Name:	MacBook Pro
  Model Identifier:	MacBookPro7,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	3 MB
  Memory:	4 GB
  Bus Speed:	1.07 GHz
  Boot ROM Version:	MBP71.0039.B05
  SMC Version (system):	1.62f5
  Serial Number (system):	W80140U3ATM
  Hardware UUID:	183BD947-DFF3-5C0E-9C39-5AA0A03467FC
  Sudden Motion Sensor:
  State:	Enabled

```

Serial-ATA
```

NVidia MCP89 AHCI:

  Vendor:	NVidia
  Product:	MCP89 AHCI
  Link Speed:	3 Gigabit
  Negotiated Link Speed:	1.5 Gigabit
  Description:	AHCI Version 1.30 Supported

TOSHIBA MK2555GSXF:

  Capacity:	250.06 GB (250,059,350,016 bytes)
  Model:	TOSHIBA MK2555GSXF                      
  Revision:	FH405B  
  Serial Number:	           3097C1H4T
  Native Command Queuing:	Yes
  Queue Depth:	32
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk0
  Rotational Rate:	5400
  Medium Type:	Rotational
  Partition Map Type:	GPT (GUID Partition Table)
  S.M.A.R.T. status:	Verified
  Volumes:
Macintosh HD:
  Capacity:	215.82 GB (215,822,106,624 bytes)
  Available:	176.2 GB (176,199,225,344 bytes)
  Writable:	Yes
  File System:	Journaled HFS+
  BSD Name:	disk0s2
  Mount Point:	/
BOOTCAMP:
  Capacity:	33.89 GB (33,892,073,472 bytes)
  Available:	33.87 GB (33,874,395,136 bytes)
  Writable:	Yes
  File System:	MS-DOS FAT32
  BSD Name:	disk0s3
  Mount Point:	/Volumes/BOOTCAMP

```

Looks like the new thing is the chipset NVIDIA MCP89.

I only planned to use OS X for movie editing. Everything else ubuntu does better (for my needs)...well apart from flash :(

---

### Post by pklat on 2010-04-20
I'll try downloading a daily build...

---

### Post by Liquidspikes on 2010-04-20
I have the MacBook Pro 15 inch Core i7 model...

I am downloading Ubuntu 10.04 beta to see what success I have... I will report back my findings soon :)

---

### Post by pklat on 2010-04-21
Same story with the latest daily build. Is there anything I can try doing from the live CD or do we just wait till linux kernel supports this chipset?

---

### Post by _mario_ on 2010-04-21
> **pklat said:**
> Same story with the latest daily build. Is there anything I can try doing from the live CD or do we just wait till linux kernel supports this chipset?

Once the lucid live CD runs, can you please attach the output of:
```

$ lspci -nnv
$ lsusb -v

```
This will by no means make anything work, but might help us to improve support, as the information obtained from within Mac OS X isn't that helpful.

However, I do have some advice if you're an advanced linux hacker: Looks like the kernel has no driver for your chipset and/or SATA adapter. As far as I know, the lucid live CD runs kernel 2.6.32-21-generic. It is some days old. 2.6.33.2 is out, and 2.6.34 is to be released.

Nevertheless, there's a kernel-ppa, that provides brand new packages, including release candidates (that are sometimes unstable). Hence, you can try to build a custom live CD (on another machine), that includes one of those newer kernel releases. (Currently, I miss the link to the documentation.) Obviously this will only make any sense, if there exists a release at all, that supports your chipset. I cannot tell without knowing the device IDs obtained via the above commands. Anyway, happy hacking. ;-)

ciao,
Mario

---

### Post by Seq on 2010-04-21
> **pklat said:**
> The only way I can start a live lucid environment is by booting from a CD and USB simultaneously. Apparently once it cannot find CD rom it looks for the USB. Live ubuntu environment works fine except for WiFi and recognising any of the SATA drives. I don't know what's new from previous versions of Macbook, but here is some info

After you manage to get booted from your CD/USB combo, output of `dmesg` would also be useful.

> **pklat said:**
> I only planned to use OS X for movie editing. Everything else ubuntu does better (for my needs)...well apart from flash :(

My SO uses OS X, and I thought flash sucked there too.

---

### Post by pklat on 2010-04-21
I attached the outputs of the 3 commands - sorry too big so had to tar.gz it. I am posting this from my MacBook running live USB/CD environment. WiFi doesn't work but rather painless tethering with nokia N82 - amazing!

I might try building a live CD when I have more time although ARCH runs kernel 2.26.33.2 and encountered the same problem - maybe more luck when 2.26.34 comes out.

---

### Post by Indi.N on 2010-04-21
I've pulled out the relevant stuff (I think):

**lspci -nvv**> 
00:0a.0 IDE interface [0101]: nVidia Corporation Device [10de:0d85] (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Apple Computer Inc. Device [106b:cb89]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
    I/O ports at 2298 [size=8]
    I/O ports at 22a4 [size=4]
    I/O ports at 2290 [size=8]
    I/O ports at 22a0 [size=4]
    I/O ports at 2280 [size=16]
    Memory at d3484000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahciNote: There would be a bit more detail instead of <access denied> if you ran it as 'sudo lspci -nvv' 

MCP89 SATA Controller ([http://pci-ids.ucw.cz/read/PC/10de/0d85](http://pci-ids.ucw.cz/read/PC/10de/0d85))
-appears to be supported by the achi sata driver ([http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html](http://cateee.net/lkddb/web-lkddb/SATA_AHCI.html))

**dmesg**> 
[    1.878641] pata_acpi 0000:00:0a.0: power state changed by ACPI to D0
[    1.878947] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 20
[    1.878951]   alloc irq_desc for 20 on node -1
[    1.878952]   alloc kstat_irqs on node -1
[    1.878957] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    1.878981] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    1.878990] pata_acpi 0000:00:0a.0: PCI INT A disabled
<snip>
[    2.338335] ahci 0000:00:0a.0: version 3.0
[    2.338349] ahci 0000:00:0a.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    2.338389]   alloc irq_desc for 27 on node -1
[    2.338391]   alloc kstat_irqs on node -1
[    2.338400] ahci 0000:00:0a.0: irq 27 for MSI/MSI-X
[    2.338436] ahci 0000:00:0a.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl IDE mode
[    2.338439] ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led pio slum part apst 
[    2.338443] ahci 0000:00:0a.0: setting latency timer to 64
<snip>
[    2.349907] scsi0 : ahci
[    2.355703] scsi1 : ahci
[    2.355794] ata1: SATA max UDMA/133 abar m8192@0xd3484000 port 0xd3484100 irq 27
[    2.355797] ata2: SATA max UDMA/133 abar m8192@0xd3484000 port 0xd3484180 irq 27
<snip>
[    7.712094] ata1: link is slow to respond, please be patient (ready=0)
[    7.756093] ata2: link is slow to respond, please be patient (ready=0)
<snip>
[   12.360102] ata1: COMRESET failed (errno=-16)
[   12.404102] ata2: COMRESET failed (errno=-16)
[   17.720094] ata1: link is slow to respond, please be patient (ready=0)
[   17.764093] ata2: link is slow to respond, please be patient (ready=0)
[   22.368101] ata1: COMRESET failed (errno=-16)
[   22.412101] ata2: COMRESET failed (errno=-16)
[   27.728094] ata1: link is slow to respond, please be patient (ready=0)
[   27.772099] ata2: link is slow to respond, please be patient (ready=0)
[   57.408101] ata1: COMRESET failed (errno=-16)
[   57.408106] ata1: limiting SATA link speed to 1.5 Gbps
[   57.452101] ata2: COMRESET failed (errno=-16)
[   57.452105] ata2: limiting SATA link speed to 1.5 Gbps
[   62.432101] ata1: COMRESET failed (errno=-16)
[   62.432106] ata1: reset failed, giving up
[   62.476101] ata2: COMRESET failed (errno=-16)
[   62.476105] ata2: reset failed, giving up
A bit of googling came up with a few kernel mailing list threads following acpi issues, and 'cold boot' (physically cold; first boot of day etc, giving slower response times).  Most of these either petered out into hardware problems or specific bug fixes, so I'm not seeing anything super obvious.

For some random voodoo/handwaving you could try an acpi=off or a libata.force=1.5Gbps 

I'm quite curious about all this, as my MBP is supposed to arrive soon.. 

:)

---

### Post by Liquidspikes on 2010-04-21
I downloaded and tried to run Ubuntu 10.40 beta 2, it wouldn't even boot... It freezes at the Ubuntu boot screen.

I did ACPI=OFF option too... same issue. I will try a daily build.

Happy Hacking! :)

---

### Post by pklat on 2010-04-21
> 
Note: There would be a bit more detail instead of <access denied> if you ran it as 'sudo lspci -nvv' 


it looks a bit different this time:

```

00:0a.0 0101: 10de:0d85 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: 106b:cb89
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 27
	Region 0: I/O ports at 2298 [size=8]
	Region 1: I/O ports at 22a4 [size=4]
	Region 2: I/O ports at 2290 [size=8]
	Region 3: I/O ports at 22a0 [size=4]
	Region 4: I/O ports at 2280 [size=16]
	Region 5: Memory at d3484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [8c] SATA HBA <?>
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
		Address: 00000000fee0100c  Data: 41a1
	Kernel driver in use: ahci
	Kernel modules: ahci

```

> For some random voodoo/handwaving you could try an acpi=off or a libata.force=1.5Gbps 

no luck :(

---

### Post by alexmurray on 2010-04-21
Probably hanging on nouveau - try boot params:

```

nouveau.noaccel=1 blacklist=vga16fb

```

---

### Post by pklat on 2010-04-22
> **alexmurray said:**
> Probably hanging on nouveau - try boot params:

```

nouveau.noaccel=1 blacklist=vga16fb

```

It doesn't detect SATA drives, that's not a graphics problem.

---

### Post by khanku on 2010-04-22
Hello all,

i ran in the same problem as pklat trying to install GNU/Linux on my MacBookPro7,1 since I got it last week.

This is more of a recapitulatory post / a sharing of my own experience.

I basically came to the same point: the SATA bus doesn't work properly, thus rendering the hard drive as well as the DVD reader unusable; booting from USB works, but the problem remains the same.
Altough the nVidia MCP89 chipset seems to be supported (see ahci.c since 2.6.29-rc6), it doesn't semm to work as expected.
I tried multiple Live-CDs with no luck. I also built a custom 2.6.33.2 kernel and booted with it... same thing :(

Seeing the minor changes made to ahci.c for MCP89 "support", I'm wondering if this isn't more of a preliminary work for supporting this chipset than anything else.

---

### Post by produnis on 2010-04-23
> **khanku said:**
> booting from USB works...
how did you make it work?

I'am struggling with USB-Live Stick since Karmic..

Creating a Live-Stick for 9.04 was no problem... but since Karmic I never made it work..

---

### Post by khanku on 2010-04-23
I made a bootable USB stick with the "usb-creator-gtk" utility from lucid.
I also tried with Slax6 Live-CD + USB.
Both worked.

---

### Post by abel_bcn on 2010-04-23
I'm getting mine on monday so I'll be investigating as well.

Glad to see I'm not the only one that can't live without Ubuntu on my new (and first) mbp!

Cheers!

---

### Post by produnis on 2010-04-23
> **khanku said:**
> I made a bootable USB stick with the "usb-creator-gtk" utility from lucid.
I also tried with Slax6 Live-CD + USB.
Both worked.

Just to get this rigth:
1. You booted your Mac with a Lucid Live-CD

2. Within the Live-Session, you plugged in a USB-Stick

3. Then, you started usb-creator-gtk  and created the Stick

4. You rebooted your Mac
------

And now?
You plugg in the Stick and boot the Mac from it? How does it work? Did you press the ALT-Key and could select the stick?

Because thats the tricky thing with me. Without having rEFIt installed within OSX, my MacbookPro4,1 won't recognize the stick at boot-time. 
Having rEFIt installed, my Mac shows it within the EFI-Menu. Till Karmic, I could then boot from the stick following this tutorial:
[http://ubuntuforums.org/showthread.php?t=1261747](http://ubuntuforums.org/showthread.php?t=1261747)
You can see from that tutorial, that it is/was a damm hack to get it run...

...and now nothing else needs to be done to create a Live-USB-Apple-Stick?
Cannot imagine that... or is it due to your "new" model Macbook7,1 (and me having a 4,1)

---

### Post by khanku on 2010-04-23
I have rEFIt installed, and boots from the CD using rEFIt boot menu.
At this time the CD is inserted (obviously) and the USB stick plugged.
I know Slax6 searches for the stick to use by design (faster, persistent changes, etc.) and I'm guessing that Ubuntu does the same thing or falls back to using the stick because it cannot find any CD/HDD.

---

### Post by hyperbole on 2010-04-24
Same story here.

MacBookPro7,1 purchased a few days ago. 

Tried both, Karmic and Lucid RC.


When booting off the internal DVD drive livecd loading process drops you into busybox and complains that no drive detected.

Booting of external USB DVD drive takes you into Livecd environment on both Karmic and Lucid RC and I did not have to change acpi mode or any other kernel parameters, goes straight through with default settings.

Wireless works in both after activating "Broadcom B43 wireless driver" via propriety drivers menu. 

But hard drive is not detected!!!! 

"fdisk -l" and Gparted dont show anything

---

### Post by kosumi68 on 2010-04-24
> **pklat said:**
> I attached the outputs of the 3 commands - sorry too big so had to tar.gz it. I am posting this from my MacBook running live USB/CD environment. WiFi doesn't work but rather painless tethering with nokia N82 - amazing!

I might try building a live CD when I have more time although ARCH runs kernel 2.26.33.2 and encountered the same problem - maybe more luck when 2.26.34 comes out.

It would also be useful to get some more information about the SMC; if you would follow [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and post the result here, that would be great.

Cheers!

---

### Post by pklat on 2010-04-27
> **kosumi68 said:**
> It would also be useful to get some more information about the SMC; if you would follow [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096) and post the result here, that would be great.

Cheers!

hi, here is the output:

```
ubuntu@ubuntu:~$ sudo dmidecode -s system-product-name
MacBookPro7,1

```

```
ubuntu@ubuntu:~/Downloads$ sudo ./applesmc-test.sh 
accelerometer: present, readable, output: (-3,15,260)
fan:           present, readable, output: 2000
light:         present, readable, output: (1,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 28750
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 31500
 temperature:           readable, output: 58250
 temperature:           readable, output: 51500
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 48750
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      4

```

```
ubuntu@ubuntu:~/Downloads$ sudo ./scan-smc.sh 
0: #KEY [4-ui32] 00000141 [...A]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0d80 [..]
8: ACID [8-ch8*] 85d67f7ec003100c [...~....]
9: ACIN [1-flag] 01 [.]
10: ACLM [1-ui8 ] 55 [U]
11: AL! [2-ui16] 0000 [..]
12: ALA0 [6-{ala] ca1effd602d9 [......]
13: ALA1 [6-{ala] 30a4021f0315 [0.....]
14: ALA2 [6-{ala] 0cea02d40396 [......]
15: ALA3 [6-{ala] 0389036103dc [...a..]
16: ALA4 [6-{ala] 00ee03bc0400 [......]
17: ALA5 [6-{ala] 04fcfff30400 [......]
18: ALAT [4-{alt] 002b0308 [.+..]
19: ALI0 [4-{ali] 04000f00 [....]
20: ALI1 [4-{ali] 00000000 [....]
21: ALP0 [4-ui16] 13330780 [.3..]
22: ALP1 [4-ui16] 00000000 [....]
23: ALRV [2-ui16] 0001 [..]
24: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
25: ALSF [2-fp1f] 2646 [&F]
26: ALSL [2-ui16] 001c [..]
27: ALT0 [2-ui16] 0000 [..]
28: ALT1 [2-ui16] 0000 [..]
29: ALTH [10-{alr] 00320070025200140041 [.2.p.R...A]
30: ALV0 [10-{alv] 0101017700df00070a76 [...w.....v]
31: ALV1 [10-{alv] 00010000000000000000 [..........]
32: AUPO [1-ui8 ] 00 [.]
33: B0AC [2-si16] 0000 [..]
34: B0AV [2-ui16] 30f7 [0.]
35: B0Ad [2-ui16] 0000 [..]
36: B0Al [2-ui16] ffff [..]
37: B0Am [1-ui8 ] 10 [.]
38: B0Ar [1-ui8 ] 00 [.]
39: B0As [1-ui8 ] 00 [.]
40: B0At [2-ui16] 0960 [.`]
41: B0Au [2-ui16] 0960 [.`]
42: B0Az [1-ui8 ] 00 [.]
43: B0BI [1-hex_] 51 [Q]
44: B0CM [2-ui16] 0158 [.X]
45: B0CT [2-ui16] 0008 [..]
46: B0FC [2-ui16] 1678 [.x]
47: B0FV [2-ui16] 0201 [..]
48: B0LI [2-ui16] 7fff [..]
49: B0PS [2-ui16] 0000 [..]
50: B0RI [2-ui16] 0000 [..]
51: B0RM [2-ui16] 1675 [.u]
52: B0St [2-ui16] 40e0 [@.]
53: B0TF [2-ui16] ffff [..]
54: BATP [1-flag] 00 [.]
55: BBAD [1-flag] 00 [.]
56: BBIN [1-flag] 01 [.]
57: BC1V [2-ui16] 1052 [.R]
58: BC2V [2-ui16] 1052 [.R]
59: BC3V [2-ui16] 1052 [.R]
60: BCHA [1-ui8 ] 02 [.]
61: BCHB [1-ui8 ] 01 [.]
62: BCHF [1-ui8 ]
63: BCHG [1-ui8 ]
64: BCHL [1-ui8 ]
65: BCHO [1-ui8 ] 1f [.]
66: BCHP [1-ui8 ] 06 [.]
67: BCHR [1-ui8 ] 3a [:]
68: BCHT [1-ui8 ] 06 [.]
69: BCHX [1-ui8 ] 01 [.]
70: BCLM [1-ui8 ] 64 [d]
71: BCMV [2-ui16] 1052 [.R]
72: BEMB [1-flag] 01 [.]
73: BFCT [2-ui16] 0000 [..]
74: BILB [1-ui8 ] 1f [.]
75: BILO [2-ui8 ] 1f09 [..]
76: BNCM [1-ui8 ]
77: BNCR [1-ui8 ] 04 [.]
78: BNum [1-ui8 ] 01 [.]
79: BRSC [2-ui16] 0064 [.d]
80: BSAC [1-ui8 ] 33 [3]
81: BSIn [1-hex_] 42 [B]
82: BTIL [2-ui16] 0680 [..]
83: BTTI [1-ui8 ] 02 [.]
84: BTVI [1-ui8 ] 02 [.]
85: BTVR [1-ui8 ] 01 [.]
86: BTVT [1-ui8 ] 01 [.]
87: BWLM [1-ui8 ] 00 [.]
88: CHBI [2-ui16] 0000 [..]
89: CHBV [2-ui16] 3138 [18]
90: CHGC [2-ui16] 0062 [.b]
91: CHGD [1-flag]
92: CHGI [2-ui16] 0000 [..]
93: CHGV [2-ui16] 3130 [10]
94: CHPV [2-si16] 3130 [10]
95: CLK! [1-ui8 ] 00 [.]
96: CLKC [10-{clc] 00000e1000000e10198c [..........]
97: CLKH [8-{clh] 0000708000011940 [..p....@]
98: CLKS [2-fp1f] 8000 [..]
99: CLKT [4-ui32] 000099cd [....]
100: CLSD [2-ui16] ffff [..]
101: CLWK [2-ui16] 0073 [.s]
102: CRCB [4-ui32] a3da51a6 [..Q.]
103: CRCU [4-ui32]
104: DPLM [3-{lim]
105: EPCA [4-ui32] 00007000 [..p.]
106: EPCF [1-flag] 01 [.]
107: EPCI [4-ui32] 04700700 [.p..]
108: EPCV [2-ui16] 0001 [..]
109: EPMA [4-ch8*] 00006080 [..`.]
110: EPMI [1-ui8 ] 00 [.]
111: EPUA [4-ui32] 00006000 [..`.]
112: EPUF [1-flag] 01 [.]
113: EPUI [4-ui32] 04700001 [.p..]
114: EPUV [2-ui16] 0001 [..]
115: EVCT [2-ui16] 0404 [..]
116: EVMD [4-ui32]
117: EVRD [32-ch8*] f606010000008aea7102ff0002008bde2303fa004800f1662304f7004900e2a4 [........q.......#...H..f#...I...]
118: F0Ac [2-fpe2] 1f4e [.N]
119: F0ID [16-{fds] 00000a00457868617573742020000000 [....Exhaust ...]
120: F0Mn [2-fpe2] 1f40 [.@]
121: F0Mt [2-ui16] 0000 [..]
122: F0Mx [2-fpe2] 60e0 [`.]
123: F0Tg [2-fpe2] 1f40 [.@]
124: FMAx [2-fpe2] 2d0b [-.]
125: FNum [1-ui8 ] 01 [.]
126: FPDc [2-fp79] 32c8 [2.]
127: FPVK [1-ui8 ] 03 [.]
128: FPhz [2-si16]
129: FS! [2-ui16] 0000 [..]
130: G3WD [1-flag] 00 [.]
131: HBWK [1-flag] 00 [.]
132: HDBS [1-ui8 ] 01 [.]
133: HDST [4-hex_] 00000000 [....]
134: HDSW [4-hex_] 00370036 [.7.6]
135: IC0C [2-sp78] 056c [.l]
136: IC0R [2-sp4b] 0539 [.9]
137: IC0c [2-ui16] 1c00 [..]
138: IC0r [2-ui16] 2840 [(@]
139: ID0R [2-sp5a] 05de [..]
140: ID0r [2-ui16] 2f80 [/.]
141: IN0C [2-sp69] 0b62 [.b]
142: IN0c [2-ui16] 2c00 [,.]
143: IN1R [2-sp4b] 01f1 [..]
144: IN1r [2-ui16] 0580 [..]
145: IP0R [2-sp5a] 00b3 [..]
146: IP0r [2-ui16] 0500 [..]
147: LAcN [1-ui8 ]
148: LAtN [2-ui16]
149: LC2D [2-ui16] d1da [..]
150: LC2E [2-ui16] d1da [..]
151: LCCN [1-ui8 ] ab [.]
152: LCCQ [1-ui8 ] 00 [.]
153: LCKA [1-ui8 ] 55 [U]
154: LCSA [1-ui8 ] b8 [.]
155: LCTN [1-ui8 ] 46 [F]
156: LCTQ [1-ui8 ] 5b [[]
157: LDI2 [1-ui8 ] 01 [.]
158: LDSP [1-flag]
159: LEDC [1-ui8 ] 00 [.]
160: LEDT [2-ui16] 8100 [..]
161: LEIC [1-ui8 ] 00 [.]
162: LEID [32-ui16] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
163: LET0 [4-ui32] 00000000 [....]
164: LET1 [4-ui32] 00000000 [....]
165: LET2 [4-ui32] 00000000 [....]
166: LKSB [2-{lkb]
167: LS! [1-ui8 ] 00 [.]
168: LSCF [10-{lsc] 00c80190800002020020 [......... ]
169: LSDD [8-{lsd] 0002000300030019 [........]
170: LSDU [8-{lsd] 0003000200140003 [........]
171: LSFD [6-{lsf] 00000004008c [......]
172: LSFU [6-{lsf] 00000004008c [......]
173: LSLB [2-{pwm] ffff [..]
174: LSLF [2-{pwm] 0000 [..]
175: LSLN [2-{pwm] ffff [..]
176: LSOF [1-flag] 01 [.]
177: LSOO [1-flag]
178: LSPV [2-{pwm] 0000 [..]
179: LSRB [1-flag]
180: LSSB [2-{lso]
181: LSSE [1-flag] 01 [.]
182: LSSS [2-{lso]
183: LSSV [2-ui16] ffff [..]
184: LSUP [1-ui8 ]
185: MACA [4-ui32] 00000000 [....]
186: MACM [1-flag] 01 [.]
187: MACR [32-ch8*]
188: MLIA [2-ui16] 0000 [..]
189: MLIR [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
190: MLSR [2-ui16] 03e8 [..]
191: MLTM [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
192: MOCF [2-ui16] 8000 [..]
193: MOCN [2-ui16] e0f8 [..]
194: MOHC [1-ui8 ] 3d [=]
195: MOHD [1-ui8 ] 14 [.]
196: MOHT [2-sp78] 01c0 [..]
197: MOLD [1-ui8 ] 14 [.]
198: MOLT [2-sp78] 0060 [.`]
199: MOST [2-ui16] 8003 [..]
200: MOVX [2-sp78] fffd [..]
201: MOVY [2-sp78] 000d [..]
202: MOVZ [2-sp78] 00ff [..]
203: MO_X [2-sp78] fffb [..]
204: MO_Y [2-sp78] 000f [..]
205: MO_Z [2-sp78] 0100 [..]
206: MSAL [1-ui8 ] 4b [K]
207: MSAb [2-ui16] 0000 [..]
208: MSAc [2-fp88] 0000 [..]
209: MSAf [2-fp6a] 0000 [..]
210: MSAg [2-fp88] 0000 [..]
211: MSAm [2-fp88] 0000 [..]
212: MSBC [2-ui16] 0000 [..]
213: MSBP [2-ui16] 0c32 [.2]
214: MSBc [2-ui16] 0004 [..]
215: MSBp [2-ui16] 0c32 [.2]
216: MSDI [1-flag] 01 [.]
217: MSDW [1-flag]
218: MSG3 [1-flag] 00 [.]
219: MSLD [1-ui8 ] 00 [.]
220: MSPA [2-fp6a] 0000 [..]
221: MSPC [1-ui8 ] 05 [.]
222: MSPS [2-ui16] 0001 [..]
223: MSSD [1-si8 ] 05 [.]
224: MSSE [2-ui16] 0000 [..]
225: MSSF [4-ui32] 00000000 [....]
226: MSSG [4-ui32] 00000000 [....]
227: MSSP [1-si8 ] 05 [.]
228: MSSS [1-{mss] 00 [.]
229: MSTC [2-ui16] 0000 [..]
230: MSTM [1-ui8 ] 01 [.]
231: MSTc [1-ui8 ] 00 [.]
232: MSTg [1-ui8 ] 00 [.]
233: MSTm [1-ui8 ] 00 [.]
234: MSWR [1-ui8 ]
235: MSXC [4-ch8*] 00000000 [....]
236: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
237: MSXK [32-ch8*] 0102030405060708090a00000000000000000000000000000000000000000000 [................................]
238: MSXN [1-ui8 ] 0a [.]
239: MSXS [4-ch8*] 02060508 [....]
240: MSXb [1-ui8 ] 00 [.]
241: MSXc [4-ch8*] 00000000 [....]
242: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
243: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f10f0f1f2f3000000000000000000000000 [................................]
244: MSXm [2-ui16] 0008 [..]
245: MSXn [1-ui8 ] 14 [.]
246: MSXs [4-ui32] 01031009 [....]
247: NACK [1-ui8 ]
248: NATJ [1-ui8 ] 00 [.]
249: NATi [2-ui16] 0000 [..]
250: NOPB [1-ui8 ] 00 [.]
251: NTOK [1-ui8 ]
252: ONMI [1-ui8 ] 00 [.]
253: PB0R [2-sp78] 0231 [.1]
254: PC0C [2-sp78] 0716 [..]
255: PC0R [2-sp78] 099f [..]
256: PD0R [2-sp78] 19b5 [..]
257: PHPC [2-sp78] 0f74 [.t]
258: PN0C [2-sp78] 0577 [.w]
259: PN1C [2-sp78] 005d [.]]
260: PTHC [2-sp78] 20e4 [ .]
261: RBr [8-ch8*] 6272616e63680000 [branch..]
262: REV [6-{rev] 01620f000005 [.b....]
263: RMde [1-char] 41 [A]
264: RPlt [8-ch8*] 6b36000000000000 [k6......]
265: RSvn [4-ui32] 00000000 [....]
266: RVBF [6-{rev] 01620f000005 [.b....]
267: RVUF [6-{rev] 01620f000005 [.b....]
268: SAS! [4-hex_] 0000f7f3 [....]
269: SBF [2-hex_] 0000 [..]
270: SBFC [2-hex_] 0000 [..]
271: SBS! [2-ui16]
272: SCIA [2-ui16] 03f8 [..]
273: SCII [1-ui8 ] 00 [.]
274: SCIL [1-ui8 ] 00 [.]
275: SDAF [2-ui16] 0000 [..]
276: SDAS [2-ui16] 0000 [..]
277: SDRd [2-ui16]
278: SFBR [1-ui8 ] 04 [.]
279: SIP [1-ui8] 01 [.]
280: SIS! [2-hex_]
281: SIT! [2-hex_]
282: SIU! [2-hex_]
283: SM0x [2-ui16] 7f40 [.@]
284: SM0y [2-ui16] 82c0 [..]
285: SM0z [2-ui16] b2c0 [..]
286: SMBC [6-ch8*]
287: SMBG [1-ui8 ]
288: SMBR [32-ch8*]
289: SMBS [2-ch8*]
290: SMBW [32-ch8*]
291: SPH0 [2-ui16] 0000 [..]
292: SPHR [4-ui32] 00000000 [....]
293: SPHS [1-ui8 ] 00 [.]
294: SPHT [2-ui16] 0000 [..]
295: SPHZ [1-ui8]
296: SPS! [4-hex_] 00000000 [....]
297: TB0T [2-sp78] 1f19 [..]
298: TB1T [2-sp78] 1f19 [..]
299: TB2T [2-sp78] 1e4c [.L]
```

---

### Post by kosumi68 on 2010-04-28
Thank you for the data - apparently the number of registers has increased well beyond what the scan script looks at, so all temperature registers are not shown in the list. Please either download the new version of scan-smc.sh from the same place where you got it, or simply change the value in the script to "END=350", and resubmit. Thanks!

---

### Post by pklat on 2010-04-28
sorry, here it is again

```
ubuntu@ubuntu:~/Downloads$ sudo dmidecode -s system-product-name
MacBookPro7,1

```

```
ubuntu@ubuntu:~/Downloads$ sudo ./applesmc-test.sh 
accelerometer: present, readable, output: (6,16,258)
fan:           present, readable, output: 2000
light:         present, readable, output: (1,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           not readable
 temperature:           readable, output: 31000
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 31750
 temperature:           readable, output: 60000
 temperature:           readable, output: 53250
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           not readable
 temperature:           readable, output: 51000
performance:   reading all temperatures
 fail frequency:        1.000
 reads per second:      4

smc-fan:  Mt type C

```

```
ubuntu@ubuntu:~/Downloads$ sudo ./scan-smc.sh
0: #KEY [4-ui32] 00000141 [...A]
1: $Adr [4-ui32] 00000300 [....]
2: $Num [1-ui8 ] 01 [.]
3: +LKS [1-flag] 07 [.]
4: ACCL [1-ui8 ]
5: ACEN [1-ui8 ] 01 [.]
6: ACFP [1-flag] 01 [.]
7: ACIC [2-ui16] 0d80 [..]
8: ACID [8-ch8*] 85d67f7ec003100c [...~....]
9: ACIN [1-flag] 01 [.]
10: ACLM [1-ui8 ] 55 [U]
11: AL! [2-ui16] 0000 [..]
12: ALA0 [6-{ala] ca1effd602d9 [......]
13: ALA1 [6-{ala] 30a4021f0315 [0.....]
14: ALA2 [6-{ala] 0cea02d40396 [......]
15: ALA3 [6-{ala] 0389036103dc [...a..]
16: ALA4 [6-{ala] 00ee03bc0400 [......]
17: ALA5 [6-{ala] 04fcfff30400 [......]
18: ALAT [4-{alt] 002b0308 [.+..]
19: ALI0 [4-{ali] 04000f00 [....]
20: ALI1 [4-{ali] 00000000 [....]
21: ALP0 [4-ui16] 13330780 [.3..]
22: ALP1 [4-ui16] 00000000 [....]
23: ALRV [2-ui16] 0001 [..]
24: ALSC [16-{alc] 00c8009603e8000f0001015e1d030106 [...........^....]
25: ALSF [2-fp1f] 1c08 [..]
26: ALSL [2-ui16] 0013 [..]
27: ALT0 [2-ui16] 0000 [..]
28: ALT1 [2-ui16] 0000 [..]
29: ALTH [10-{alr] 00320070025200140041 [.2.p.R...A]
30: ALV0 [10-{alv] 010100e900870004ebc4 [..........]
31: ALV1 [10-{alv] 00010000000000000000 [..........]
32: AUPO [1-ui8 ] 00 [.]
33: B0AC [2-si16] 0000 [..]
34: B0AV [2-ui16] 30ae [0.]
35: B0Ad [2-ui16] 0000 [..]
36: B0Al [2-ui16] ffff [..]
37: B0Am [1-ui8 ] 10 [.]
38: B0Ar [1-ui8 ] 00 [.]
39: B0As [1-ui8 ] 00 [.]
40: B0At [2-ui16] 0960 [.`]
41: B0Au [2-ui16] 0960 [.`]
42: B0Az [1-ui8 ] 00 [.]
43: B0BI [1-hex_] 51 [Q]
44: B0CM [2-ui16] 0158 [.X]
45: B0CT [2-ui16] 0008 [..]
46: B0FC [2-ui16] 1676 [.v]
47: B0FV [2-ui16] 0201 [..]
48: B0LI [2-ui16] 0f80 [..]
49: B0PS [2-ui16] 0000 [..]
50: B0RI [2-ui16] 0000 [..]
51: B0RM [2-ui16] 15d8 [..]
52: B0St [2-ui16] 40e0 [@.]
53: B0TF [2-ui16] ffff [..]
54: BATP [1-flag] 00 [.]
55: BBAD [1-flag] 00 [.]
56: BBIN [1-flag] 01 [.]
57: BC1V [2-ui16] 103a [.:]
58: BC2V [2-ui16] 103a [.:]
59: BC3V [2-ui16] 103a [.:]
60: BCHA [1-ui8 ] 02 [.]
61: BCHB [1-ui8 ] 01 [.]
62: BCHF [1-ui8 ]
63: BCHG [1-ui8 ]
64: BCHL [1-ui8 ]
65: BCHO [1-ui8 ] 1f [.]
66: BCHP [1-ui8 ] 0a [.]
67: BCHR [1-ui8 ] 3a [:]
68: BCHT [1-ui8 ] 06 [.]
69: BCHX [1-ui8 ] 01 [.]
70: BCLM [1-ui8 ] 64 [d]
71: BCMV [2-ui16] 103a [.:]
72: BEMB [1-flag] 01 [.]
73: BFCT [2-ui16] 0000 [..]
74: BILB [1-ui8 ] 1f [.]
75: BILO [2-ui8 ] 1f07 [..]
76: BNCM [1-ui8 ]
77: BNCR [1-ui8 ] 04 [.]
78: BNum [1-ui8 ] 01 [.]
79: BRSC [2-ui16] 0062 [.b]
80: BSAC [1-ui8 ] 33 [3]
81: BSIn [1-hex_] 42 [B]
82: BTIL [2-ui16] 0680 [..]
83: BTTI [1-ui8 ] 02 [.]
84: BTVI [1-ui8 ] 02 [.]
85: BTVR [1-ui8 ] 01 [.]
86: BTVT [1-ui8 ] 01 [.]
87: BWLM [1-ui8 ] 00 [.]
88: CHBI [2-ui16] 0000 [..]
89: CHBV [2-ui16] 3138 [18]
90: CHGC [2-ui16] 0062 [.b]
91: CHGD [1-flag]
92: CHGI [2-ui16] 0000 [..]
93: CHGV [2-ui16] 3130 [10]
94: CHPV [2-si16] 3130 [10]
95: CLK! [1-ui8 ] 00 [.]
96: CLKC [10-{clc] 00000e1000000e10198c [..........]
97: CLKH [8-{clh] 0000708000011940 [..p....@]
98: CLKS [2-fp1f] 198c [..]
99: CLKT [4-ui32] 00014a41 [..JA]
100: CLSD [2-ui16] ffff [..]
101: CLWK [2-ui16] 0073 [.s]
102: CRCB [4-ui32] a3da51a6 [..Q.]
103: CRCU [4-ui32]
104: DPLM [3-{lim]
105: EPCA [4-ui32] 00007000 [..p.]
106: EPCF [1-flag] 01 [.]
107: EPCI [4-ui32] 04700700 [.p..]
108: EPCV [2-ui16] 0001 [..]
109: EPMA [4-ch8*] 00006080 [..`.]
110: EPMI [1-ui8 ] 00 [.]
111: EPUA [4-ui32] 00006000 [..`.]
112: EPUF [1-flag] 01 [.]
113: EPUI [4-ui32] 04700001 [.p..]
114: EPUV [2-ui16] 0001 [..]
115: EVCT [2-ui16] 0101 [..]
116: EVMD [4-ui32]
117: EVRD [32-ch8*] f6060100000132c77102ff0002008bde2303fa004800f1662304f7004900e2a4 [......2.q.......#...H..f#...I...]
118: F0Ac [2-fpe2] 1f3a [.:]
119: F0ID [16-{fds] 00000a00457868617573742020000000 [....Exhaust ...]
120: F0Mn [2-fpe2] 1f40 [.@]
121: F0Mt [2-ui16] 0000 [..]
122: F0Mx [2-fpe2] 60e0 [`.]
123: F0Tg [2-fpe2] 1f40 [.@]
124: FMAx [2-fpe2] 3ce8 [<.]
125: FNum [1-ui8 ] 01 [.]
126: FPDc [2-fp79] 332c [3,]
127: FPVK [1-ui8 ] 03 [.]
128: FPhz [2-si16]
129: FS! [2-ui16] 0000 [..]
130: G3WD [1-flag] 00 [.]
131: HBWK [1-flag] 00 [.]
132: HDBS [1-ui8 ] 00 [.]
133: HDST [4-hex_] 00000000 [....]
134: HDSW [4-hex_] 00390038 [.9.8]
135: IC0C [2-sp78] 054b [.K]
136: IC0R [2-sp4b] 052f [./]
137: IC0c [2-ui16] 1600 [..]
138: IC0r [2-ui16] 1b00 [..]
139: ID0R [2-sp5a] 05d0 [..]
140: ID0r [2-ui16] 2f40 [/@]
141: IN0C [2-sp69] 0b63 [.c]
142: IN0c [2-ui16] 2c40 [,@]
143: IN1R [2-sp4b] 01e4 [..]
144: IN1r [2-ui16] 0580 [..]
145: IP0R [2-sp5a] 00b3 [..]
146: IP0r [2-ui16] 04c0 [..]
147: LAcN [1-ui8 ]
148: LAtN [2-ui16]
149: LC2D [2-ui16] f46e [.n]
150: LC2E [2-ui16] f46e [.n]
151: LCCN [1-ui8 ] ce [.]
152: LCCQ [1-ui8 ] 32 [2]
153: LCKA [1-ui8 ] 26 [&]
154: LCSA [1-ui8 ] 49 [I]
155: LCTN [1-ui8 ] 76 [v]
156: LCTQ [1-ui8 ] 11 [.]
157: LDI2 [1-ui8 ] 01 [.]
158: LDSP [1-flag]
159: LEDC [1-ui8 ] 00 [.]
160: LEDT [2-ui16] 8100 [..]
161: LEIC [1-ui8 ] 00 [.]
162: LEID [32-ui16] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
163: LET0 [4-ui32] 00000000 [....]
164: LET1 [4-ui32] 00000000 [....]
165: LET2 [4-ui32] 00000000 [....]
166: LKSB [2-{lkb]
167: LS! [1-ui8 ] 00 [.]
168: LSCF [10-{lsc] 00c80190800002020020 [......... ]
169: LSDD [8-{lsd] 0002000300030019 [........]
170: LSDU [8-{lsd] 0003000200140003 [........]
171: LSFD [6-{lsf] 00000004008c [......]
172: LSFU [6-{lsf] 00000004008c [......]
173: LSLB [2-{pwm] ffff [..]
174: LSLF [2-{pwm] 0000 [..]
175: LSLN [2-{pwm] ffff [..]
176: LSOF [1-flag] 01 [.]
177: LSOO [1-flag]
178: LSPV [2-{pwm] 0000 [..]
179: LSRB [1-flag]
180: LSSB [2-{lso]
181: LSSE [1-flag] 01 [.]
182: LSSS [2-{lso]
183: LSSV [2-ui16] ffff [..]
184: LSUP [1-ui8 ]
185: MACA [4-ui32] 00000000 [....]
186: MACM [1-flag] 01 [.]
187: MACR [32-ch8*]
188: MLIA [2-ui16] 0000 [..]
189: MLIR [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
190: MLSR [2-ui16] 03e8 [..]
191: MLTM [32-ch8*] 0000000000000000000000000000000000000000000000000000000000000000 [................................]
192: MOCF [2-ui16] 8000 [..]
193: MOCN [2-ui16] e0f8 [..]
194: MOHC [1-ui8 ] 3d [=]
195: MOHD [1-ui8 ] 14 [.]
196: MOHT [2-sp78] 01c0 [..]
197: MOLD [1-ui8 ] 14 [.]
198: MOLT [2-sp78] 0060 [.`]
199: MOST [2-ui16] 8003 [..]
200: MOVX [2-sp78] 0002 [..]
201: MOVY [2-sp78] 000c [..]
202: MOVZ [2-sp78] 00fe [..]
203: MO_X [2-sp78] 0002 [..]
204: MO_Y [2-sp78] 000b [..]
205: MO_Z [2-sp78] 0101 [..]
206: MSAL [1-ui8 ] 4b [K]
207: MSAb [2-ui16] 0000 [..]
208: MSAc [2-fp88] 0000 [..]
209: MSAf [2-fp6a] 0000 [..]
210: MSAg [2-fp88] 0000 [..]
211: MSAm [2-fp88] 0000 [..]
212: MSBC [2-ui16] 0000 [..]
213: MSBP [2-ui16] 0af7 [..]
214: MSBc [2-ui16] 0000 [..]
215: MSBp [2-ui16] 0af7 [..]
216: MSDI [1-flag] 01 [.]
217: MSDW [1-flag]
218: MSG3 [1-flag] 00 [.]
219: MSLD [1-ui8 ] 00 [.]
220: MSPA [2-fp6a] 0000 [..]
221: MSPC [1-ui8 ] 05 [.]
222: MSPS [2-ui16] 0001 [..]
223: MSSD [1-si8 ] 03 [.]
224: MSSE [2-ui16] 0000 [..]
225: MSSF [4-ui32] 00000000 [....]
226: MSSG [4-ui32] 00000000 [....]
227: MSSP [1-si8 ] 05 [.]
228: MSSS [1-{mss] 00 [.]
229: MSTC [2-ui16] 0000 [..]
230: MSTM [1-ui8 ] 01 [.]
231: MSTc [1-ui8 ] 00 [.]
232: MSTg [1-ui8 ] 00 [.]
233: MSTm [1-ui8 ] 00 [.]
234: MSWR [1-ui8 ]
235: MSXC [4-ch8*] 00000000 [....]
236: MSXD [16-ch8*] 00000000000000000000000000000000 [................]
237: MSXK [32-ch8*] 0102030405060708090a00000000000000000000000000000000000000000000 [................................]
238: MSXN [1-ui8 ] 0a [.]
239: MSXS [4-ch8*] 02060508 [....]
240: MSXb [1-ui8 ] 00 [.]
241: MSXc [4-ch8*] 00000000 [....]
242: MSXd [16-ch8*] 00000000000000000000000000000000 [................]
243: MSXk [32-ch8*] 0102030405060708090a0b0c0d0e0f10f0f1f2f3000000000000000000000000 [................................]
244: MSXm [2-ui16] 0008 [..]
245: MSXn [1-ui8 ] 14 [.]
246: MSXs [4-ui32] 01031009 [....]
247: NACK [1-ui8 ]
248: NATJ [1-ui8 ] 00 [.]
249: NATi [2-ui16] 0000 [..]
250: NOPB [1-ui8 ] 00 [.]
251: NTOK [1-ui8 ]
252: ONMI [1-ui8 ] 00 [.]
253: PB0R [2-sp78] 0232 [.2]
254: PC0C [2-sp78] 07d4 [..]
255: PC0R [2-sp78] 0a8a [..]
256: PD0R [2-sp78] 1ad1 [..]
257: PHPC [2-sp78] 1068 [.h]
258: PN0C [2-sp78] 057f [..]
259: PN1C [2-sp78] 005e [.^]
260: PTHC [2-sp78] 20e4 [ .]
261: RBr [8-ch8*] 6272616e63680000 [branch..]
262: REV [6-{rev] 01620f000005 [.b....]
263: RMde [1-char] 41 [A]
264: RPlt [8-ch8*] 6b36000000000000 [k6......]
265: RSvn [4-ui32] 00000000 [....]
266: RVBF [6-{rev] 01620f000005 [.b....]
267: RVUF [6-{rev] 01620f000005 [.b....]
268: SAS! [4-hex_] 0000f7f3 [....]
269: SBF [2-hex_] 0000 [..]
270: SBFC [2-hex_] 0000 [..]
271: SBS! [2-ui16]
272: SCIA [2-ui16] 03f8 [..]
273: SCII [1-ui8 ] 00 [.]
274: SCIL [1-ui8 ] 00 [.]
275: SDAF [2-ui16] 0000 [..]
276: SDAS [2-ui16] 0000 [..]
277: SDRd [2-ui16]
278: SFBR [1-ui8 ] 04 [.]
279: SIP [1-ui8] 01 [.]
280: SIS! [2-hex_]
281: SIT! [2-hex_]
282: SIU! [2-hex_]
283: SM0x [2-ui16] 8100 [..]
284: SM0y [2-ui16] 8300 [..]
285: SM0z [2-ui16] b280 [..]
286: SMBC [6-ch8*]
287: SMBG [1-ui8 ]
288: SMBR [32-ch8*]
289: SMBS [2-ch8*]
290: SMBW [32-ch8*]
291: SPH0 [2-ui16] 0000 [..]
292: SPHR [4-ui32] 00000000 [....]
293: SPHS [1-ui8 ] 00 [.]
294: SPHT [2-ui16] 0000 [..]
295: SPHZ [1-ui8]
296: SPS! [4-hex_] 00000000 [....]
297: TB0T [2-sp78] 1fb3 [..]
298: TB1T [2-sp78] 1fb3 [..]
299: TB2T [2-sp78] 1ecc [..]
300: TC0D [2-sp78] 4160 [A`]
301: TC0P [2-sp78] 35c0 [5.]
302: TN0D [2-sp78] 3ca0 [<.]
303: TN0P [2-sp78] 2f00 [/.]
304: TN0S [2-sp78] 4600 [F.]
305: TN1D [2-sp78] 4600 [F.]
306: TN1F [2-sp78] 4600 [F.]
307: TN1G [2-sp78] 5a00 [Z.]
308: TN1S [2-sp78] 4600 [F.]
309: Th1H [2-sp78] 3300 [3.]
310: Ts0P [2-sp78] 1e10 [..]
311: Ts0S [2-sp78] 2b27 [+']
312: UPRC [2-ui16] 0845 [.E]
313: VC0C [2-sp3c] 1149 [.I]
314: VC0c [2-ui16] 5780 [W.]
315: VN0C [2-sp3c] 0f39 [.9]
316: VN0c [2-ui16] 49c0 [I.]
317: VP0R [2-sp5a] 3245 [2E]
318: VP0r [2-ui16] a2c0 [..]
319: WKEN [1-ui8] 00 [.]
320: zDBG [1-ui8] 00 [.]

```

---

### Post by kosumi68 on 2010-04-28
Enclosed is a DKMS package with an applesmc including support for MBP71. Decompress, install, reboot. Please report the output of test script again; it should now show zero or very few errors. Thanks!

---

### Post by pklat on 2010-04-28
> **kosumi68 said:**
> Enclosed is a DKMS package with an applesmc including support for MBP71. Decompress, install, reboot. Please report the output of test script again; it should now show zero or very few errors. Thanks!

Sorry, how do I install to a live CD/USB?

---

### Post by kosumi68 on 2010-04-28
> **pklat said:**
> Sorry, how do I install to a live CD/USB?

Move the file to the desktop, chose "extract here", then double-click, that should give you instructions how to install the package.

To avoid the rebooting, do this instead:
```

sudo rmmod applesmc
sudo modprobe applesmc
dmesg | grep applesmc:

```

The output should show "MacBook Pro 7" if everything worked out correctly.

---

### Post by pklat on 2010-04-29
of course :) thanks.

did as instructed, here is the new output

```
ubuntu@ubuntu:~/Downloads$ sudo ./applesmc-test.sh 
accelerometer: present, readable, output: (-5,17,257)
fan:           present, readable, output: 2000
light:         present, readable, output: (1,0)
leds:          present,
 led:                   readable, output: 0
temperatures:  present,
 temperature:           readable, output: 62750
 temperature:           readable, output: 90000
 temperature:           readable, output: 62750
 temperature:           readable, output: 45000
 temperature:           readable, output: 26500
 temperature:           readable, output: 37000
 temperature:           readable, output: 27750
 temperature:           readable, output: 27750
 temperature:           readable, output: 26750
 temperature:           readable, output: 53250
 temperature:           readable, output: 47250
 temperature:           readable, output: 52500
 temperature:           readable, output: 43750
 temperature:           readable, output: 62750
 temperature:           readable, output: 62000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      50

smc-fan:  Mt type C

```

---

### Post by kosumi68 on 2010-04-29
Great, we have support for MBP71. If you want to appear with a Tested-by: in the Linux kernel logs, send me a private message with your name and email. Thanks!

---

### Post by mistertim on 2010-04-29
Hey,

Many thanks for this, but would someone be able to point a n00b in the direction of some instructions about how to use the above dkms file? 

Thanks in advance,

Tim

EDIT for clarification, as this sounds like a pretty silly question without: given that it's not possible to load the LiveCD, given the lack of CD-ROM drive support, is it possible to install the dkms as part of the install process, or do i need to create a custom liveCD with it included somehow?

---

### Post by ninocass on 2010-04-30
also interested in this, have a new 7,1 that is just itching to have ubuntu installed on it!

---

### Post by DJ.Khaos on 2010-04-30
I got the same problem on my new macbook pro (7.1). Waiting for the solution. Thanks

---

### Post by cronin1024 on 2010-04-30
> **ninocass said:**
> also interested in this, have a new 7,1 that is just itching to have ubuntu installed on it!

> **DJ.Khaos said:**
> I got the same problem on my new macbook pro (7.1). Waiting for the solution. Thanks

Me three. I don't understand why 10.04 was released with this pretty serious bug - now we're stuck with defective LTS discs for the next two years.

---

### Post by ninocass on 2010-04-30
Managed to hook up an LG drive via an IDE to USB converter. Install battles through until it comes up with

No drives detected, and gives me a list of drivers, I've selected "none of these" from the list and put the above attachment on a USB drive, I then get an error saying no kernel modules were found

I can boot into the live OS and installed the DKMS package but i still cant access the partition.  My guess is to add the modules for the whilst in the live OS and install ubuntu on the partition, reboot into the live OS again and chroot the partition and put the modules on, i could be talking out my *** tho....

any ideas?

---

### Post by khanku on 2010-04-30
> **ninocass said:**
> I can boot into the live OS and installed the DKMS package but i still cant access the partition.

I'm not sure how installing applesmc is supposed to help make sata work... ?

Kind of off-topic note:
FreeBSD 7.3 sees both drives, which seem to work flawlessly.

---

### Post by ninocass on 2010-04-30
not sure myself i was grasping at straws to be honest lol

i dont want to switch to free BSD can we get an ubuntu work around?

nino

---

### Post by ivanhoe1024 on 2010-05-01
Hi everybody, I have the same problem, too. I succeded to boot live cd only using cd + usb key and holding down the C key. Than, I can't see my HD in the installer nor in Gparted or other command-line tools... It seems that it's not a "macbook-only" problem, I found in the italian forum some other people that are unable to see their HD, even though they're PC users... Any idea???

---

### Post by ivanhoe1024 on 2010-05-01
> **ivanhoe1024 said:**
> Hi everybody, I have the same problem, too. I succeded to boot live cd only using cd + usb key and holding down the C key. Than, I can't see my HD in the installer nor in Gparted or other command-line tools... It seems that it's not a "macbook-only" problem, I found in the italian forum some other people that are unable to see their HD, even though they're PC users... Any idea???

PS. in the italian forum they succeded to install ubuntu 10.04 on those computers I mentioned above. They used ubuntu 10.04 64 bit alternate cd, and answered "no" when the installer asked them if they'd like to use raid tecnology. I haven't tried this yet, if anyone of you'll do it, please let us know!

---

### Post by ninocass on 2010-05-01
> **ivanhoe1024 said:**
> PS. in the italian forum they succeded to install ubuntu 10.04 on those computers I mentioned above. They used ubuntu 10.04 64 bit alternate cd, and answered "no" when the installer asked them if they'd like to use raid tecnology. I haven't tried this yet, if anyone of you'll do it, please let us know!

Is the macbook not a 32 bit processor?

I have ran through the 32 bit alternate and desktop install dvds but it still wont pick up the HDD ( i didnt see any mention of RAID tho)  were the using a standard build or a nightly?  Downloading the 64 bit alt image now, blank CD in the drive ready to go ;)

Cheers

---

### Post by abel_bcn on 2010-05-01
Is this a problem strictly with Lucid, or no version of Ubuntu can be installed?

---

### Post by ninocass on 2010-05-01
> **abel_bcn said:**
> Is this a problem strictly with Lucid, or no version of Ubuntu can be installed?

Tried 9.10 and and 7.10 and no HDD drive detected.  Alsi tried the alt  amd64 of 10.04 and still no drives, it didnt give me the option of selecting raid or not so not sure what version the italian guys are using

---

### Post by ivanhoe1024 on 2010-05-02
> **ninocass said:**
> Tried 9.10 and and 7.10 and no HDD drive detected.  Alsi tried the alt  amd64 of 10.04 and still no drives, it didnt give me the option of selecting raid or not so not sure what version the italian guys are using

Ok, I tried myself the alternate 64 bit, and it can't find /dev/cdrom, nor a module to use. I tried also the live installer after installing applesmc downloaded from this thread, and nothing... I really don't know what to try now...

---

### Post by linuxopjemac on 2010-05-02
I would wait until the linux world has a driver for the sata drive...You can't expect to have Linux on the newest of machines.

---

### Post by ivanhoe1024 on 2010-05-02
> **linuxopjemac said:**
> I would wait until the linux world has a driver for the sata drive...You can't expect to have Linux on the newest of machines.

I know, I know, It's just a bit frustrating... :(

---

### Post by ninocass on 2010-05-02
What's the best way of finding out with the modules have been added?  Keep an eye on the changelogs for daily builds or is there a Linux on mac project group?

Cheers

---

### Post by linuxopjemac on 2010-05-02
Just read the Ubuntu forums, I guess as soon as someone finds it out, he/she will post it here...

---

### Post by ninocass on 2010-05-02
Mention of the sata MCP89 device here

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc8/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc8/CHANGES)

and also in a patch:

[http://package-import.ubuntu.com/diffs/pciutils](http://package-import.ubuntu.com/diffs/pciutils)

---

### Post by turawk on 2010-05-03
The shipping kernel in Ubuntu 10.04 is 2.6.32.  Has anybody tried booting with a newer kernel?

I've been eying the 13" Macbook Pro 7,1 but won't get it if I can't boot from the hard drive.  Do they set an EFI firmware password at the Apple store?

I was thinking of making a custom livecd with a newer kernel, perhaps 2.6.34-rc6...

I looked at the Italian forum thread and saw that there was only one person in the thread with this Macbook and he did not succeed in installing Ubuntu.

---

### Post by ivanhoe1024 on 2010-05-04
> **turawk said:**
> The shipping kernel in Ubuntu 10.04 is 2.6.32.  Has anybody tried booting with a newer kernel?

I've been eying the 13" Macbook Pro 7,1 but won't get it if I can't boot from the hard drive.  Do they set an EFI firmware password at the Apple store?

I was thinking of making a custom livecd with a newer kernel, perhaps 2.6.34-rc6...

I looked at the Italian forum thread and saw that there was only one person in the thread with this Macbook and he did not succeed in installing Ubuntu.
Hi!! Here I am! :D

---

### Post by ninocass on 2010-05-04
> **turawk said:**
> The shipping kernel in Ubuntu 10.04 is 2.6.32.  Has anybody tried booting with a newer kernel?

I've been eying the 13" Macbook Pro 7,1 but won't get it if I can't boot from the hard drive.  Do they set an EFI firmware password at the Apple store?

I was thinking of making a custom livecd with a newer kernel, perhaps 2.6.34-rc6...

I looked at the Italian forum thread and saw that there was only one person in the thread with this Macbook and he did not succeed in installing Ubuntu.

someone tried 2.6.33.2

[http://ubuntuforums.org/showpost.php?p=9157326&postcount=22](http://ubuntuforums.org/showpost.php?p=9157326&postcount=22)

---

### Post by khanku on 2010-05-05
> **ninocass said:**
> someone tried 2.6.33.2

[http://ubuntuforums.org/showpost.php?p=9157326&postcount=22](http://ubuntuforums.org/showpost.php?p=9157326&postcount=22)

Correct, I did.
I tried 2.6.34-rc6 and 2.6.29-rc6 as well.
(2.6.29-rc6 is the first kernel with MCP89 support mentioned in ahci.h)

---

### Post by ottosolocinque on 2010-05-05
any news?

---

### Post by spook on 2010-05-06
I just got my first Macbook Pro, the 7,1 model and I'd love to install Ubuntu on it.  Does anyone know how long it normally takes to get the necessary drivers working?  Will we have to wait for 10.10?

I'll just have to stick with OS X for the moment.

---

### Post by grapz on 2010-05-06
I couldn't find any bugreports on this, so I made one at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576601](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576601) and also an upstream bug at [https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

---

### Post by ivanhoe1024 on 2010-05-07
> **khanku said:**
> Correct, I did.
I tried 2.6.34-rc6 and 2.6.29-rc6 as well.
(2.6.29-rc6 is the first kernel with MCP89 support mentioned in ahci.h)

I suppose the results are not so positive, are they?? Just a question: how did you use a different kernel with a live version??

---

### Post by grapz on 2010-05-07
> **ivanhoe1024 said:**
> Just a question: how did you use a different kernel with a live version??

You can rebuild the LiveCD images.
A quick Google search led me to this:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I'm plannig on doing this today with the latest RC kernel, just to get some logs from that one too.

---

### Post by ivanhoe1024 on 2010-05-07
> **grapz said:**
> You can rebuild the LiveCD images.
A quick Google search led me to this:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I'm plannig on doing this today with the latest RC kernel, just to get some logs from that one too.

Thanks for the answer... I'm waiting your test before to try by myself someting like this... I hope you'll get it work!! Let us know about your results! Good Luck ):P

---

### Post by cosmicappuccino on 2010-05-07
I have this problem too :(

---

### Post by autoexec on 2010-05-07
Has anyone been able to determine what would be involved in fixing this?
Is it a minor revision on another chip we already have drivers for, or will this need a whole new driver?.

I havn't actually bought the hardware yet due to this issue

---

### Post by peterisza on 2010-05-08
Here's my lspci output from OSX:
```

00:0a.0 SATA controller: nVidia Corporation Unknown device 0d88 (rev a2) (prog-if 01 [AHCI 1.0])
        Subsystem: Apple Computer Inc. Unknown device cb89

```

The device id seems to be listed in ahci.c even in the 2.6.32 kernel:
```

	{ PCI_VDEVICE(NVIDIA, 0x0d88), board_ahci },		/* MCP89 */

```

I thought it could be as simple as adding a device ID to the driver, but it isn't. :(

---

### Post by autoexec on 2010-05-08
> **khanku said:**
> FreeBSD 7.3 sees both drives, which seem to work flawlessly.

At the very least, this is encouraging. We can look at the freebsd driver if need be.

---

### Post by shazow on 2010-05-08
Same problem here.

I'll try and rebuild the LiveCD with the latest kernel/patches soon.

- shazow

---

### Post by ivanhoe1024 on 2010-05-09
> **shazow said:**
> Same problem here.

I'll try and rebuild the LiveCD with the latest kernel/patches soon.

- shazow

Hi, did you try?? Please give us good news!!! :(

---

### Post by grapz on 2010-05-09
I haven't been having any luck yet.

When customizing the LiveCD with the latest upstream kernel, I'm having problems booting the LiveCD:
mounting aufs on /root failed: no such device
aufs mount failed

If any of you know how to fix this issue, please let me know, so I can test this against the latest upstream kernel.

---

### Post by grapz on 2010-05-10
An update:

I've booted my MBP7,1 with the 2.6.34-RC7 kernel, but still no disks detected :(

---

### Post by kwangchin on 2010-05-10
I am not familiar with recompiling kernel but after some readings, I found that MCP89 has been supported since kernel 2.6.30 but not sure which revision. You can check out at its source at drivers/ata/ahci.c

With this, I believe the original kernel, which is 2.6.32 in Ubuntu 10.04 has this supported as well. Has anyone tried to compile with the config "CONFIG_SATA_AHCI=y" as it was pre-compiled as modules.

---

### Post by grapz on 2010-05-11
kwangchin;
Yeah, it has supported MCP89 since 2.6.29-rc6.

I'll give it a go tonight to compile with "CONFIG_SATA_AHCI=y"

---

### Post by kwangchin on 2010-05-11
Tried several times on 2.6.34-rc7 but keep getting Kernel panic lmao :confused:

---

### Post by grapz on 2010-05-11
> **kwangchin said:**
> Tried several times on 2.6.34-rc7 but keep getting Kernel panic lmao :confused:

With your own compiled 2.6.34-rc7 kernel that has "CONFIG_SATA_AHCI=y"?

---

### Post by kwangchin on 2010-05-11
Yes, probably because of RC? I am trying with 2.6.33.3 right now :)

---

### Post by khanku on 2010-05-11
> **grapz said:**
> With your own compiled 2.6.34-rc7 kernel that has "CONFIG_SATA_AHCI=y"?

I build a (gentoo based) LiveCD each time there is a new kernel and try booting my MacBookPro7,1 using it... with no luck so far.

Sadly I don't have much time to test this more thoroughly, so here is the ISO if someone is interested:
[http://server7.chavant.info/khanku/genlive/](http://server7.chavant.info/khanku/genlive/)
(just copy the content of the ISO on an USB stick to boot the system despite the CD drive not being found)

---

### Post by kwangchin on 2010-05-11
> **khanku said:**
> I build a (gentoo based) LiveCD each time there is a new kernel and try booting my MacBookPro7,1 using it... with no luck so far.

Sadly I don't have much time to test this more thoroughly, so here is the ISO if someone is interested:
[http://server7.chavant.info/khanku/genlive/](http://server7.chavant.info/khanku/genlive/)
(just copy the content of the ISO on an USB stick to boot the system despite the CD drive not being found)

Thanks khanku. I would still prefer Ubuntu 10.04 LTS :tongue:

---

### Post by kwangchin on 2010-05-12
Anyone know how to add/compile aufs in kernel? I noticed there is a directory `ubuntu/aufs` in `linux-headers-2.6.32-21-generic` thats probably what we need?

---

### Post by grapz on 2010-05-12
Yes, you'll need to compile with aufs. Dunno how you do it, I've never done it.

What I've done to do testing, is that I've installed Ubuntu to a 4GB USB stick. Then I've installed the newest kernel and stuff.

The only things you need to remeber is to boot this on the MBP, you'll need to have a LiveCD in the CD Drive, boot from that, and in the boot menu for Ubuntu, select boot from first harddisk.

Also, the USB stick must be in the same USB port that you had it in when you installed Ubuntu to it, because it seems like the aft port always becomes sdb and the front port always becomes sdc.

---

### Post by DeMiNe0 on 2010-05-12
Just got my MBP7,1 and I have the same issues. Glad I'm not alone here. I'll start testing out new kernels as they come out.

---

### Post by autoexec on 2010-05-12
Is there any news about other hardware (eg, wifi) in it working? Is that testable at this stage?

---

### Post by grapz on 2010-05-12
Wifi works with restricted drivers (Broadcom STA drivers).

It seems (as far as I've seen) with the LiveCD, that CPU scaling/fan control isn't working properly. When I use the LiveCD, the CPU seems to be running on max, without any fan control, thus the computer being really hot.

Also, all of the hotkeys aren't working in the LiveCD, but we'll probably be able to debug that once we got a running system installed.

---

### Post by dustingram on 2010-05-13
I'd recommend that anyone who wishes to be kept up-to-date on this issue should subscribe to the relevant bug report (that grapz created):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576601/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576601/)

---

### Post by ciscler on 2010-05-14
Hey,

are there some new news?

---

### Post by kswan on 2010-05-14
Back at post #37 kosumi68 said that this was solved, right?

If you install the DKMS module in post #33, are you able to see your drives (at least with fdisk -l)?

---

### Post by grapz on 2010-05-14
> **kswan said:**
> Back at post #37 kosumi68 said that this was solved, right?

If you install the DKMS module in post #33, are you able to see your drives (at least with fdisk -l)?

This is just for all the stuff, like FAN controll, temp sensors and stuff, not the SATA controller (as far as I know).

---

### Post by kosumi68 on 2010-05-14
Yes. Following the development in the launchpad bug 576601, as suggested, is good advice.

---

### Post by cosmicappuccino on 2010-05-14
> **kosumi68 said:**
> Yes. Following the development in the launchpad bug 576601, as suggested, is good advice.

Sorry, I don't understand how to use your file :confused: 

It seem the applesmc file is meant to be installed on Linux? How do we install it on Linux if the Ubuntu CD isn't booting?

Thanks very much for any advice!

---

### Post by grapz on 2010-05-14
> **cosmicappuccino said:**
> Sorry, I don't understand how to use your file :confused: 

It seem the applesmc file is meant to be installed on Linux? How do we install it on Linux if the Ubuntu CD isn't booting?

Thanks very much for any advice!

You need to install Ubuntu to a USB stick, and then you can install the AppleSMC files.

---

### Post by cosmicappuccino on 2010-05-14
> **grapz said:**
> You need to install Ubuntu to a USB stick, and then you can install the AppleSMC files.

Thanks very much for the advice - it all makes more sense now!

However, I'm still having problems... as you can tell, I'm pretty new to this, so I guess I'm not doing it right. I've succeeded at booting Ubuntu from my memory stick, going into "Try Ubuntu 10.04" mode, and then installing the applesmc files.

Then I click the "Install Ubuntu 10.04" icon. The first few steps are fine, but at the partitioning step, no partitions appear in the partition list, i.e. it still doesn't seem to find the hard drive. :(

Could someone please tell me what I'm missing here?

---

### Post by grapz on 2010-05-14
> **cosmicappuccino said:**
> Thanks very much for the advice - it all makes more sense now!

However, I'm still having problems... as you can tell, I'm pretty new to this, so I guess I'm not doing it right. I've succeeded at booting Ubuntu from my memory stick, going into "Try Ubuntu 10.04" mode, and then installing the applesmc files.

Then I click the "Install Ubuntu 10.04" icon. The first few steps are fine, but at the partitioning step, no partitions appear in the partition list, i.e. it still doesn't seem to find the hard drive. :(

Could someone please tell me what I'm missing here?

That's because the applesmc doesn't fix the hard drive issue as far as I've seen. applesmc makes the fan control, temp sensors and other stuff like that work, but the issue with the hard disk not being detected is a kernel issue.

The reason you would want to install Ubuntu to an USB stick (not just boot the livecd, but actually install it to the USB stick), is to be able to easily test/compile kernels to fix the issue. Running Ubuntu from USB stick is very slow compared to normal.

---

### Post by ciscler on 2010-05-15
Hi,

I have the same problem with my macbook pro 7,1.
Can I do anything to help to fix the problem?

ciscler

---

### Post by grapz on 2010-05-15
> **ciscler said:**
> Hi,

I have the same problem with my macbook pro 7,1.
Can I do anything to help to fix the problem?

ciscler

Well, if you know anything about debugging the kernel, you could help out there. I don't really know much about it, but I'm gonna give it a go shortly.

Other than that, be sure to go here: [https://bugs.launchpad.net/linux/+bug/576601](https://bugs.launchpad.net/linux/+bug/576601) and click on the 'This bug affects me' at the top of the page.

---

### Post by cosmicappuccino on 2010-05-15
> **grapz said:**
> That's because the applesmc doesn't fix the hard drive issue as far as I've seen. applesmc makes the fan control, temp sensors and other stuff like that work, but the issue with the hard disk not being detected is a kernel issue.

The reason you would want to install Ubuntu to an USB stick (not just boot the livecd, but actually install it to the USB stick), is to be able to easily test/compile kernels to fix the issue. Running Ubuntu from USB stick is very slow compared to normal.

Thanks very much; understood. ^^
I somehow had the mistaken impression that it fixed the hard drive too, so thanks for clarifying.

---

### Post by autoexec on 2010-05-16
disregard this post.

---

### Post by tixetsal on 2010-05-17
Thank God I found this thread.  I have been struggling with this on a new MBP 13" for the last 4 days, trying all manner of old isos and hacks.  
I am trying to use wubi in my bootcamp partition, so that I don't have to do any rEFIt messiness.  (I have a mini that I triple-boot, but I am not willing to go through that setup again.)  
Wubi is failing for the same reason.  At least now I know that I can put this on the back-burner, as it is nothing that I am doing wrong.  Virtual Box will have to suffice until this is resolved.

Threads subscribed-to and fingers crossed...

---

### Post by garrettg84 on 2010-05-19
If this affects your computer, please sign into launchpad/create an account and click the link up top that 'This bug affects me'
 
[https://bugs.launchpad.net/linux/+bug/576601](https://bugs.launchpad.net/linux/+bug/576601)
 
According to the Launchpad site, this bug now has a high priority. It has been confirmed that there are some issues with the NVIDIA MCP89 SATA chipset/drivers that control both the HDD and CD/DVD drive. 
 
Only workarounds for right now:
1) Install Ubuntu on a USB stick, boot from the USB stick.
2) Boot the Ubuntu CD from an external CD-ROM drive.
3) Run Ubuntu in a VM. (not an option for native performance)

---

### Post by matzen on 2010-05-20
> **garrettg84 said:**
> If this affects your computer, please sign into launchpad/create an account and click the link up top that 'This bug affects me'
 
[https://bugs.launchpad.net/linux/+bug/576601](https://bugs.launchpad.net/linux/+bug/576601)
 
According to the Launchpad site, this bug now has a high priority. It has been confirmed that there are some issues with the NVIDIA MCP89 SATA chipset/drivers that control both the HDD and CD/DVD drive. 
 
Only workarounds for right now:
1) Install Ubuntu on a USB stick, boot from the USB stick.
2) Boot the Ubuntu CD from an external CD-ROM drive.
3) Run Ubuntu in a VM. (not an option for native performance)

I tried installing from a USB stick but that gave me the same error as with the CD/DVD installation...

---

### Post by garrettg84 on 2010-05-20
> **matzen said:**
> I tried installing from a USB stick but that gave me the same error as with the CD/DVD installation...
Sorry if I was not entirely clear. Install Ubuntu ON a USB stick. You will have to do this from another computer likely, or use one of the methods to create a live USB stick from within OS X.

---

### Post by luis zeni on 2010-05-20
HI, i installed ubuntu on a USB stick in another machine. In this machine it work ok.

But when i try to boot it at macbook  don't work. (i boot from cd and choose to boot in first disk.)

=/

---

### Post by turawk on 2010-05-22
I'm sure this is a long shot, but has anyone tried building and booting a kernel from the 2.6.35 git branch listed in this changelog?  There are references to MCP89 in the diff file..

[http://www.spinics.net/lists/kernel/msg1036130.html]("http://www.spinics.net/lists/kernel/msg1036130.html")

---

### Post by khanku on 2010-05-22
I'm downloading the 2.6.34-git8 patch and will be building a kernel  right away :)

UPDATE:
Sadly, it doesn't seem to work.
If you want to try for yourself: [http://server7.chavant.info/khanku/genlive/genlive64-201005221.iso](http://server7.chavant.info/khanku/genlive/genlive64-201005221.iso)

---

### Post by garrettg84 on 2010-05-22
[https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)
Looks like this bug is kernel wide. This is not simply an Ubuntu issue. Will update with more information when possible.

---

### Post by ToorJockey on 2010-05-28
How did you get FreeBSD 8.0 to work? I tried booting the 64bit ISO DVD and it didn't work. Any suggestions?

---

### Post by Locksmith_P on 2010-05-29
Having the same problem with Macbook 7,1 (2.4 C2D), It uses the same NVIDIA MCP89 SATA chipset. now testing with other kernels... sigh, i want my triple boot!

---

### Post by peterisza on 2010-05-30
Why don't you just read this thread instead of wasting your time?

> **Locksmith_P said:**
> Having the same problem with Macbook 7,1 (2.4 C2D), It uses the same NVIDIA MCP89 SATA chipset. now testing with other kernels... sigh, i want my triple boot!

---

### Post by Locksmith_P on 2010-05-30
> Why don't you just read this thread instead of wasting your time?Sorry, i should clarify: Im currently testing kernels that I have compiled myself. even with no success at least im learning something :)

---

### Post by gnudung on 2010-05-30
> **garrettg84 said:**
> If this affects your computer, please sign into launchpad/create an account and click the link up top that 'This bug affects me'
 
[https://bugs.launchpad.net/linux/+bug/576601](https://bugs.launchpad.net/linux/+bug/576601)
 

I'm new as you can see. I registered at launchpad.net, and completed the handshake. They agree I'm logged in. I can't see any text that says exactly "This bug affects me."

I posted a useless comment, signed up for the notify list, logged out, logged in but there was no uptick from 74 to 75 users affected.

Is that just the latency of the site and am I a new user who is perhaps impatient? Or should it be already saying "75"?

ADDENDUM FOR OTHER NEW USERS: the bugs.launchpad.net site does not function properly in Google Chrome or Safari (latest of each, Mac OS 10.6.3). The popup that lets you say "Yes it affects me" appears off the left side of the window in Chrome. Using Firefox, you can see it and respond.

---

### Post by kwangchin on 2010-05-30
[Kernel 2.6.35-rc1]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.35-rc1") says:

> This patch adds generic support for the MacBook Pro 7 family based on the 7,1 model.

I will try this later

---

### Post by pklat on 2010-05-31
> **kwangchin said:**
> [Kernel 2.6.35-rc1]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.35-rc1") says:



I will try this later

I believe this is in regard to the sensors and applesmc stuff kosumi68 asked me to test. Unfortunately I don't think there have been any changes to SATA controller. Still worth a shot :)

---

### Post by khanku on 2010-06-01
> **ToorJockey said:**
> How did you get FreeBSD 8.0 to work? I tried  booting the 64bit ISO DVD and it didn't work. Any suggestions?

IIRC I used FreeBSD 7.3 livefs and it worked.

---

### Post by sha.goyjo on 2010-06-01
Okay, question: Is this a bug or a wishlist? If the hardware isn't supported by the kernel version of ubuntu, I think this is a wishlist for maverick (i.e. possibly backports) rather than a "bug" proper in ubuntu.

Don't want to start a flame war, just want clarification.

---

### Post by popey on 2010-06-01
> **sha.goyjo said:**
> Okay, question: Is this a bug or a wishlist? If the hardware isn't supported by the kernel version of ubuntu, I think this is a wishlist for maverick (i.e. possibly backports) rather than a "bug" proper in ubuntu.


It's a bug given it's a currently shipping device from a well known manufacturer, and we're shipping LTS CDs which won't work on it.

However it seems to me that Apple laptops are often looked down upon by Linux developers:-

a) because Apple do strange things to seemingly standard components.
b) because it's Apple.

Not much we can do until someone upstream (kernel) takes a look at it really. I don't see this being upgraded to a high priority bug any time soon.

---

### Post by sha.goyjo on 2010-06-01
> **popey said:**
> It's a bug given it's a currently shipping device from a well known manufacturer, and we're shipping LTS CDs which won't work on it.


Okay, I guess what I'm saying is that if kernel 2.6.33-22 doesn't support ethe 7,1, and if Ubuntu ships with 2.6.32-21 (which updates to 2.6.32.22), is this a "flaw" in the LTS release or simply part of the feature freeze. It isn't like this won't be fixed, but feature freezing is part of the distro release cycle.

I don't think it's fair to say that Apple is being "looked down on" in this situation. It's not as if the kernel developers upstream aren't integrating support for the 7,1 in 2.6.35, as was shown earlier in the thread.

So I guess I have to re-ask my question. Being as it is necessary for Ubuntu to do a freeze before releasing, it is necessary for them to use a stable kernel at the time of freeze. That means that support for the newest systems is not going to be present. That's simply part of using a non-rolling release cycle. So I guess I still want to know, should we be posting this bug as a bug in the current release, or as a wishlist (IE please use kernel 2.6.35 in maverick) for the next release.

Thank you for not looking at this as argumentative, I just think that if we Linux-Mac users want to be taken seriously, it is imperative that we understand the development cycle and use proper channels. IE what can we do to get this taken care of in the proper manner by the right people.

---

### Post by popey on 2010-06-01
> **sha.goyjo said:**
> Okay, I guess what I'm saying is that if kernel 2.6.33-22 doesn't support ethe 7,1, and if Ubuntu ships with 2.6.32-21 (which updates to 2.6.32.22), is this a "flaw" in the LTS release or simply part of the feature freeze. It isn't like this won't be fixed, but feature freezing is part of the distro release cycle.

It's a flaw in the kernel which ships with the LTS release. Therefore it's a flaw in the LTS release.

> **sha.goyjo said:**
> I don't think it's fair to say that Apple is being "looked down on" in this situation. It's not as if the kernel developers upstream aren't integrating support for the 7,1 in 2.6.35, as was shown earlier in the thread.

I'm not saying that in this particular instance Apple is being looked down on. I am saying that on the whole in general many Linux developers seem (from my experience) to be anti-Apple. Indeed one comment in the Ubuntu Kernel channel reinforced this. 

It's not that they don't want this fixed, and dont want to help in doing that. I think it's more that _they_ think Mac owners probably believe the platform (and hence the issue) is more widespread than it really is. 

> **sha.goyjo said:**
> So I guess I have to re-ask my question. Being as it is necessary for Ubuntu to do a freeze before releasing, it is necessary for them to use a stable kernel at the time of freeze. That means that support for the newest systems is not going to be present. That's simply part of using a non-rolling release cycle. So I guess I still want to know, should we be posting this bug as a bug in the current release, or as a wishlist (IE please use kernel 2.6.35 in maverick) for the next release.

The kernel team pick a kernel to be supported for that release. In the future they may backport patches to that kernel if they make sense. For example if the issue with the Macboook7,1 turns out to be a simple kernel patch which exists in 2.6.35 then it may well be ported back to 2.6.32. Until that fix exists there's little we can do I'm afraid.

Also note that LTS releases get point releases through their life which may include updated kernels. The next point release for 10.04 (10.04.01) is due on July 29th 2010.

[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

> **sha.goyjo said:**
> Thank you for not looking at this as argumentative, I just think that if we Linux-Mac users want to be taken seriously, it is imperative that we understand the development cycle and use proper channels. IE what can we do to get this taken care of in the proper manner by the right people.

We've done pretty much all we can. Short of buying a 13" MacBook7,1 and putting it in front of a kernel developer.. anyone got $1000 spare? :)

---

### Post by sha.goyjo on 2010-06-01
> **popey said:**
> It's a flaw in the kernel which ships with the LTS release. Therefore it's a flaw in the LTS release.


I hate to beat a dead horse here, but I still don't understand how hardware where support hasn't been added yet constitutes a "flaw". Maybe you could explain it to me. As far as I know, a flaw would be if we hardware we claimed to support didn't function. But how can hardware we don't claim to support not working be considered a flaw in the OS.

Please explain in more detail what it is you mean with your usage of the word "flaw" because I think that is where our misunderstanding is arising from.

Thanks,
Jason

---

### Post by popey on 2010-06-01
> **sha.goyjo said:**
> I hate to beat a dead horse here, but I still don't understand how hardware where support hasn't been added yet constitutes a "flaw". Maybe you could explain it to me. As far as I know, a flaw would be if we hardware we claimed to support didn't function. But how can hardware we don't claim to support not working be considered a flaw in the OS.

It's not new hardware. It's a chip-set which is already supported in the Linux kernel, not a new device lacking support entirely, but a device for which there is support, but it's broken in this laptop.

From conversations I've had with the kernel team it seems there's something quirky going on (possibly timing related) which causes the device to sleep, not wake up, not be recognised correctly. Which it is, is still to be determined.

---

### Post by sha.goyjo on 2010-06-01
Alright, thanks for clearing that up. From the conversation earlier on it seemed like device support simply hadn't been added yet. Thanks for the clarification.

---

### Post by twinoatl on 2010-06-02
I propose 50€ to get this bug solved:
[http://www.cofundos.org/project.php?id=187](http://www.cofundos.org/project.php?id=187)

Please add your bid here (even 1€/$ would be cool).

---

### Post by linuxopjemac on 2010-06-02
cool that one can bid on such a project ;)
win-win situation

---

### Post by garrettg84 on 2010-06-11
It appears that a dirty patch has been created for the SATA drivers. With this news, it shouldn't be too long until an entire solution is available. Stay posted!


Updated Info:
[https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

---

### Post by AnotherFineMess on 2010-06-12
I've been having the same problem as the rest of the users in this thread. Ive purchaced the 7,1 macbook and i cant install ubuntu linux. Ive been keeping an eye on this thread and the bugzilla page and i saw that the ata_generic driver seems to work in order to recognize the mc89 sata chip on the macs. The driver is a C file there are some people who have tested it on their 7,1 macs. I dont know how to build a custom kernel and load the driver modules in order to successfully install ubuntu. So please, i know many people know how to do this as the user below did, which does not explain in depth which steps are needed in order to finally install ubuntu. **I please ask someone to compose a mini step by step guide for compiling and loading this driver module in a custom kernel. **

This quote from the last message sent in the above kernel bug page [https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

> Comment #22 From  Benoit Gschwind   2010-06-11 23:11:51  -------

Good news, I find a way to use MCP89 IDE on MacBookPro 7,1.

To make it working I use the ata_generic driver patched and disable other
drivers (see config file summited). With this patch I can mount and read
partition of MacOS X.

I summited the new ata_generic.c file. This patch is durty please do not use it
without reviewed it.

---

### Post by koencalliauw on 2010-06-20
This seems to affect the new Mac Mini unibody too.

/K

---

### Post by norfair on 2010-06-21
> **koencalliauw said:**
> This seems to affect the new Mac Mini unibody too.

/K

Ugh. I was just about to order one with the hopes of removing OSX completely and installing 10.04. Rats. Why must Apple be the only one out there to build small, efficient, quiet, but capable desktops? How I wish Canonical would find a partner (other than Dell) to make slick Ubuntu built systems. I'll keep checking in to see if there's improvement on the mini front. Thanks for this quick bit of info!

---

### Post by Scrubru on 2010-06-24
I was considering buying one and wiping out the OSX. Now it seems that the problem pertains to the SATA driver. All that CPU fan speed stuff can be solved by installing that DKMS package...

I'm not familiar with SATA though, but has anyone ever tried to install Lucid on the solid-state drive? Furthermore, mbp 7,1 comes with an Intel HD card and an Nvidia G330M, seems like a hybrid-graphics layout. If Ubuntu is successfully installed, will it be able to power both cards?

---

### Post by Jason Brownbridge on 2010-06-25
Someone has put up an iso for installing 64bit lucid at [https://help.ubuntu.com/community/MacBookPro7-1/Lucid]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid"). I have updated the guide to include how I got my sound and display/keyboard brightness settings working. Also at the moment my battery life seems pretty good (6-7 hours with wifi surfing) so Lucid looks promising :)

---

### Post by grantgalitz on 2010-07-08
It seems that there are two filepaths that can be written and read from to get lcd backlighting and led keyboard lighting.

/sys/class/leds/smc::kbd_backlight/brightness (for the keyboard lighting)
/sys/class/backlight/nvidia_backlight/brightness (for the lcd backlight)

The lcd backlight has a range from 0 to 44000, while the keyboard lighting has a range from 0 to 255.

Writing small shell scripts and binding them to keyboard shortcuts seems to work, as I tried this on my new macbook pro.

---

### Post by grantgalitz on 2010-07-08
These two scripts seem to be an alternative method, since pommed is causing issues for a few people I've talked to.

A script for the keyboard:
```
#!/bin/bash
LIGHTLEVEL=$(cat /sys/class/leds/smc::kbd_backlight/brightness)
LEVELDIFFERENCE=15
MAXVALUE=255
MINVALUE=0
if [ $LIGHTLEVEL -ge $MINVALUE ] && [ $LIGHTLEVEL -le $MAXVALUE ]
    then
    TOTAL=`expr $MAXVALUE`
    case $1 in
        up)
            TOTAL=`expr $LIGHTLEVEL + $LEVELDIFFERENCE`;;
        down)
            TOTAL=`expr $LIGHTLEVEL - $LEVELDIFFERENCE`;;
    esac
    if [ $TOTAL -ge $MINVALUE ] && [ $TOTAL -le $MAXVALUE ]
        then
        echo $TOTAL > /sys/class/leds/smc::kbd_backlight/brightness
    else
        echo "New value out of range: $TOTAL";
    fi
else
    echo 'System light level out of min/max range (Hardware might not be matching script)';
fi
```And a script for the lcd backlight:
```
#!/bin/bash
LIGHTLEVEL=$(cat /sys/class/backlight/nvidia_backlight/brightness)
LEVELDIFFERENCE=400
MAXVALUE=44000
MINVALUE=0
if [ $LIGHTLEVEL -ge $MINVALUE ] && [ $LIGHTLEVEL -le $MAXVALUE ]
    then
    TOTAL=`expr $MAXVALUE`
    case $1 in
        up)
            TOTAL=`expr $LIGHTLEVEL + $LEVELDIFFERENCE`;;
        down)
            TOTAL=`expr $LIGHTLEVEL - $LEVELDIFFERENCE`;;
    esac
    if [ $TOTAL -ge $MINVALUE ] && [ $TOTAL -le $MAXVALUE ]
        then
        echo $TOTAL > /sys/class/backlight/nvidia_backlight/brightness
    else
        echo "New value out of range: $TOTAL";
    fi
else
    echo 'System light level out of min/max range (Hardware might not be matching script)';
fi
```

---

### Post by grantgalitz on 2010-07-08
Make sure you edit sudoers to allow these scripts to be used as an exception to root.
Also there are two parameters, up and down, that are passed with the command for use.
So add a keyboard shortcut for a command like: "sudo lcd_backlight up"
Passing no parameters changes to values to the maximum lighting allowed in the script.

Scripts adapted from [http://www.mabishu.com/blog/2010/06/24/macbook-pro-keyboard-backlight-keys-on-ubuntu-gnulinux/](http://www.mabishu.com/blog/2010/06/24/macbook-pro-keyboard-backlight-keys-on-ubuntu-gnulinux/)

---

### Post by maximus3d on 2010-07-15
In case if anyone is interested...

Just downloaded Opensuse 11.3 - no problems with booting up from LiveCD, Partitioner can see all drives. Everything is working, except mouse-track pad: pointer moves, but because of multi-touch it is not possible to drag/resize... USB mice works fine.

---

### Post by maximus3d on 2010-07-16
Update on OpenSUSE: can not make wireless work, can not install Nvidia drivers, HDD is slow.

I may be wrong, but it seems to me, that there are no proper drivers yet for the Macbook Pro 7.1 hardware, except ones for MacOS.

---

### Post by tixetsal on 2010-07-16
> **maximus3d said:**
> Update on OpenSUSE: can not make wireless work, can not install Nvidia drivers, HDD is slow.

I may be wrong, but it seems to me, that there are no proper drivers yet for the Macbook Pro 7.1 hardware, except ones for MacOS.

Can anyone else verify this?

---

### Post by Logoman500 on 2010-07-18
Hi,
i have MacBookPro7,1 with 2.66 Intel Core 2 Due /4GB 1067 mHz DDR3 /500 GB  Seagate 7200 RPM with Mac OS X Snow Leopard Version 10.6.4.
i install rEFit than make three partition than i restart my mac than i install Windows 7 and it's Ok.
to install Ubuntu i do everything and i come with one solution, i used external DVD drive when I get to the the part 4 of the installation the one you can't choose the partition for Ubuntu you will not going to see the SATA Drive so i open my macbook pro and remove the HDD then i install other HDD than i running my mac i press alt and i chose the external DVD when it's open first picture of Ubuntu i connect the the SATA HDD (the original on) thru the USB using enclosure case when reach  
the partition selection for Ubuntu now i see it and i continue the instillation until the end.
now i remove the SATA HDD (the original on) from the enclosure case, then i install it in my macbook pro again now everything ok but i see these error :


Gave up waiting for root device,  Common problems:
	- Boot args (cat /proc/cmdline)
		- Check rootdelay= (did the system wait long enough?)
		- Check root= (did the system wait for the right device?)
	- Missing modules (cat /proc/modules; is /dev)
ALERT! 	/dev/disk/by-uuid/4aae0f87-e74b-b500-347319f057c3 does not
opping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) _



i hope some one can fix these error 
i think because i install Ubuntu to external hard drive and i use it internal .

---

### Post by maximus3d on 2010-07-18
tried daily build from:
[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)
works perfectly!

---

### Post by Logoman500 on 2010-07-19
> **maximus3d said:**
> tried daily build from:
[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)
works perfectly!

it's working fine \\:D/

---

### Post by delijati on 2010-07-19
Is someone able to get a resolution > 1440x 900 on a external monitor .. i only get a black screen.

[https://help.ubuntu.com/community/MacBookPro7-1/Lucid#External%20Monitor](https://help.ubuntu.com/community/MacBookPro7-1/Lucid#External%20Monitor)

---

### Post by sha.goyjo on 2010-07-19
> **pklat said:**
> ...well apart from flash :(

What does that mean? Are you having trouble with flash as well?

---

### Post by AnotherFineMess on 2010-07-20
Also working on my Macbook 7.1 13" . I've been waiting for this fix almost 2 months now. The daily build released on 19 July works almost perfect. This is just like a cool summer breeze of free software to my shinny new macbook.

There are some hardware issues a haven't found any solution yet (Bluetooth, external monitor, brightness etc) although they will be fixed through time i hope. Just need to keep a look at [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

I dont think ill be following this thread anymore so just hope everyone a good summer. Greetings from sunny Greece !

---

### Post by scullez on 2010-07-20
Does anyone know any software that can work with MBP 13" **single mic-in/audio-out port**? I want to connect external mic, because internal one is very quiet, even in maximal volume (that's one more problem).
Maybe somebody know how Apple In-Ear Headphones with Mic ([http://store.apple.com/us/product/MA850?mco=MTM3NDY3MjQ](http://store.apple.com/us/product/MA850?mco=MTM3NDY3MjQ)) works? They have single jack too.

---

### Post by mynest on 2010-07-21
thanks for you all guys, I had got the same problem, but now I have solved the problem by your suggestion. 
Appreciated!!:popcorn:

---

### Post by rodelnewbie on 2010-07-22
Hi Guys,
 
I just got my new macbook pro 7.1/ 13.3/ 4gb 250HD snow leopard ( the new one in the market) and i really want to install ubuntu but its giving me the same issues. its not recognizing the CD. it drives me all the way to selecting the language but after that its gving me an error. while reading all the comments we have in this forum as a newbie it confuses me alot :). can someone fro mthe guru's provide us newbies a step by step procedure (for dummies) how to install ubuntu. please Thanks in advance.
 
rodel

---

### Post by twinoatl on 2010-07-23
> **rodelnewbie said:**
> I just got my new macbook pro 7.1/ 13.3/ 4gb 250HD snow leopard ( the new one in the market) and i really want to install ubuntu but its giving me the same issues. its not recognizing the CD. it drives me all the way to selecting the language but after that its gving me an error. while reading all the comments we have in this forum as a newbie it confuses me alot :). can someone fro mthe guru's provide us newbies a step by step procedure (for dummies) how to install ubuntu. please Thanks in advance.

That's what the wiki page is for: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid). If you follow explanations, you will manage to install Ubuntu on your new laptop. However, there are still problems that might prevent you from enjoying your trip.

---

### Post by scullez on 2010-07-23
I've solved reboot freeze problem using this:
[http://ubuntuforums.org/showpost.php?p=8566636&postcount=5](http://ubuntuforums.org/showpost.php?p=8566636&postcount=5)

If this method worked for someone else, we can add it to the MBP7.1 wiki.

---

### Post by labaom on 2010-07-23
> **scullez said:**
> I've solved reboot freeze problem using this:
[http://ubuntuforums.org/showpost.php?p=8566636&postcount=5](http://ubuntuforums.org/showpost.php?p=8566636&postcount=5)

If this method worked for someone else, we can add it to the MBP7.1 wiki.

Doesn't seem to work for me. Can anyone help me with the brightness keys they do not work no matter what I do!

---

### Post by scullez on 2010-07-23
> **labaom said:**
> Doesn't seem to work for me.Don't forget to run update-grub after editing /etc/default/grub. Have you did that?
> **labaom said:**
>  Can anyone help me with the brightness keys they do not work no matter what I do!
You have to install and configure pommed using this wiki: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

---

### Post by labaom on 2010-07-23
> **scullez said:**
> Don't forget to run update-grub after editing /etc/default/grub. Have you did that?

You have to install and configure pommed using this wiki: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

Okay Ill try your suggestion. However the pommed thing doesn't work. I followed the steps. It seems you have done this before if you have AIM or something maybe you can help me further? I just want to use Ubuntu as much as I can and this would definitely help.

EDIT: Sorry your suggestion for refreshing grub did not work. I cannot restart.

---

### Post by scullez on 2010-07-23
> **labaom said:**
> Okay Ill try your suggestion. However the pommed thing doesn't work. I followed the steps. It seems you have done this before if you have AIM or something maybe you can help me further? I just want to use Ubuntu as much as I can and this would definitely help.

Yeah, everything described in that wiki totally works for me.
For today, I've configured everything that listed in that manual plus some power management tricks that allowed me to run my macbook for 5-7 hours on battery

---

### Post by labaom on 2010-07-23
> **scullez said:**
> Yeah, everything described in that wiki totally works for me.
For today, I've configured everything that listed in that manual plus some power management tricks that allowed me to run my macbook for 5-7 hours on battery

Can you help me via teamviewer because I would like to use Ubuntu to the maximum it would be appreciated.

---

### Post by cK-judic on 2010-07-23
> **labaom said:**
> Can you help me via teamviewer because I would like to use Ubuntu to the maximum it would be appreciated.

It'd be nice if you guys put everything in the wiki or here so that we can all use it. I'm backing up my Ubuntu install right now and then I'm going to install on my shiny new MBP.

---

### Post by cK-judic on 2010-07-23
> **labaom said:**
> Okay Ill try your suggestion. However the pommed thing doesn't work. I followed the steps. It seems you have done this before if you have AIM or something maybe you can help me further? I just want to use Ubuntu as much as I can and this would definitely help.

EDIT: Sorry your suggestion for refreshing grub did not work. I cannot restart.

I think you actually need to do update-grub2 - I did and reboot works for me.

---

### Post by ciscler on 2010-07-26
Hello,

the wiki page tells about low disk access what can you say about it. Is it really slow or should I wait before installing ubuntu?

Ciscler

---

### Post by labaom on 2010-07-26
> **ciscler said:**
> Hello,

the wiki page tells about low disk access what can you say about it. Is it really slow or should I wait before installing ubuntu?

Ciscler

It also says that claim is depreciated...

---

### Post by iammuze on 2010-08-05
hello.

i followed the documentation for the macbook 7,1, and everything was working beautifully up until the kernel header upgrades on august 5th. after the update, sound no longer works on my macbook. i checked the file /etc/modprobe.d/alsa-base.conf and found that the line "options snd-hda-intel model=mbp55" was still right where i left it.

i tried reinstalling gnome-alsamixer, to no avail. neither alsamixer nor the ubuntu sound preferences see a sound device anymore.

changing the line "options snd-hda-intel model=mbp55" to "options snd-hda-intel model=auto" gave me a dummy device in both alsamixer and the sound preferences but it did not affect my speakers or headphone jack.

this is the aptitude history for the upgrade:

```
Start-Date: 2010-08-05  01:40:07
Upgrade: 
 linux-image-2.6.32-24-generic (2.6.32-24.38, 2.6.32-24.39),
 linux-headers-2.6.32-24 (2.6.32-24.38, 2.6.32-24.39),
 gparted (0.5.1-1ubuntu2, 0.5.1-1ubuntu3),
 linux-libc-dev (2.6.32-24.38, 2.6.32-24.39),
 gdm (2.30.2.is.2.30.0-0ubuntu2, 2.30.2.is.2.30.0-0ubuntu3),
 linux-headers-2.6.32-24-generic (2.6.32-24.38, 2.6.32-24.39)
End-Date: 2010-08-05  01:40:57
```

if anyone can help me solve this i would be extremely grateful, i know the ubuntu forums are always awesome with this kind of stuff.

---

### Post by ninocass on 2010-08-09
sound, backlight and keyboard light fully working using the nightly bild and the tweaks on the wiki!

There seems to be blue-tooth support on this thread:
[http://ubuntuforums.org/showthread.php?t=1469437&highlight=BCM2046](http://ubuntuforums.org/showthread.php?t=1469437&highlight=BCM2046)

When i installed the package my mac book automatically connects to my magic mouse however hcitool doesn't display any local devices and a pan0 device is created.   After a reboot i am unable to reconnect the mouse unless I reinstall and reinstall

On a side notes does anyone know how to rebind cmd + c to copy and cmd + v to paste?

cheers

---

### Post by mac-linux on 2010-08-11
How do i execute this.... Thanks 

> **grantgalitz said:**
> These two scripts seem to be an alternative method, since pommed is causing issues for a few people I've talked to.

A script for the keyboard:
```
#!/bin/bash
LIGHTLEVEL=$(cat /sys/class/leds/smc::kbd_backlight/brightness)
LEVELDIFFERENCE=15
MAXVALUE=255
MINVALUE=0
if [ $LIGHTLEVEL -ge $MINVALUE ] && [ $LIGHTLEVEL -le $MAXVALUE ]
    then
    TOTAL=`expr $MAXVALUE`
    case $1 in
        up)
            TOTAL=`expr $LIGHTLEVEL + $LEVELDIFFERENCE`;;
        down)
            TOTAL=`expr $LIGHTLEVEL - $LEVELDIFFERENCE`;;
    esac
    if [ $TOTAL -ge $MINVALUE ] && [ $TOTAL -le $MAXVALUE ]
        then
        echo $TOTAL > /sys/class/leds/smc::kbd_backlight/brightness
    else
        echo "New value out of range: $TOTAL";
    fi
else
    echo 'System light level out of min/max range (Hardware might not be matching script)';
fi
```And a script for the lcd backlight:
```
#!/bin/bash
LIGHTLEVEL=$(cat /sys/class/backlight/nvidia_backlight/brightness)
LEVELDIFFERENCE=400
MAXVALUE=44000
MINVALUE=0
if [ $LIGHTLEVEL -ge $MINVALUE ] && [ $LIGHTLEVEL -le $MAXVALUE ]
    then
    TOTAL=`expr $MAXVALUE`
    case $1 in
        up)
            TOTAL=`expr $LIGHTLEVEL + $LEVELDIFFERENCE`;;
        down)
            TOTAL=`expr $LIGHTLEVEL - $LEVELDIFFERENCE`;;
    esac
    if [ $TOTAL -ge $MINVALUE ] && [ $TOTAL -le $MAXVALUE ]
        then
        echo $TOTAL > /sys/class/backlight/nvidia_backlight/brightness
    else
        echo "New value out of range: $TOTAL";
    fi
else
    echo 'System light level out of min/max range (Hardware might not be matching script)';
fi
```

---

### Post by bastones on 2010-08-11
> **mac-linux said:**
> How do i execute this.... Thanks

I think these are executed by creating a file in gedit with no extension (when saving it). Then go into the Terminal and type:

*cd ~/Documents*
then:
*chmod 777 file_name_here*

Then double-click the file from your Documents folder to execute the script. Don't forget to save the file to your Documents folder.

Chmod is basically changing the permissions of the file to allow it to be executed by you in the Terminal when opening the file, and ~/ is referenced to your *home* folder (the folder with your account name in it), which inside it has the Documents, Desktop and other folders, etc.

---

### Post by jazzman76063 on 2010-08-18
I was able to get 10.04 installed on my MacBook Pro 7,1 13.3" using the following process:
 
First, I installed rEFIt and partioned the drive with Disk Utility (instead of bootcamp) per the steps recommended by this article on Lifehacker: 
[http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/](http://www.lifehacker.com.au/2010/05/how-to-triple-boot-your-mac-with-windows-and-linux-no-boot-camp-required/)
 
I then downloaded the daily build of Ubuntu 10.04 from [http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)
 
I tried using a CD but when it didn't work, I ended up using Unetbootin ( [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ) to create a USB bootable disk. This will require access to Windows or another installation of Linux as Unetbootin doesn't run on Mac OS :(
 
I popped the USB drive into the computer, reboot, pressed C-key so rEFIt allowed me to choose and selected the USB drive when it appeared. Installation was pretty normal from there, and then I went thru the steps on the Community documentation ([https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)) to get everything working.
 
Notes on the Community Documentation:
I haven't tested the following things: external monitor, iSight, bluetooth
 
For wireless, I had to use the Broadcom STA driver (the proprietary driver). The free one (b43-fwcutter) does not seem to work even though it shows up in Hardware Drivers. The homepage? for the driver specifically indicates that the BCM4322 a/b/g/n models (such as the default airport card in my macbook) are not currently supported ([http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43))
 
Sound seems iffy. It seems to work over headphones, but I get no sound from the speakers themselves. Anyone have any ideas on that?
 
Edit: Nevermind...sound works.  It helped when I went back to alsamixer and unmuted the front speakers instead of just turning up the volume.

---

### Post by kcleong on 2010-12-11
Is it possible to disable the touchpad when typing? In the mouse config dialog it's not also possible to disable tap to click. I tried using synclient to disable the touchpad when typing, but synclient gives an error. Multitouch works, two/three taps, vertical/horizantal scrolling etc.

```

$ synclient -m 500
Can't access shared memory area. SHMConfig disabled?
Couldn't find synaptics properties. No synaptics driver loaded?

```

The bcm5974-dkms and xserver-xorg-input-synaptics packages are installed. The diagnostic script for the bcm5974 modules says that no synaptics driver is loaded.

```

$ /usr/src/bcm5974-1.1.7/scripts/bcm5974-diagnostics 
-----------------------------------------------------------------------
* Kernel version: 2.6.35-23-generic
* Synaptics version: 1.2.2-2ubuntu5-mactel1
* USB device: Bus 004 Device 002: ID 05ac:0237 Apple, Inc. Internal Keyboard/Trackpad (ISO)
* /lib/modules/2.6.35-23-generic/kernel/drivers/input/mouse/bcm5974.ko: exists
* /etc/modules: bcm5974 no longer explicitly listed, good
* /etc/modprobe.d/options: file not found
* /etc/modprobe.d/bcm5974: no such file, good
* /lib/modules/2.6.35-23-generic/modules.usbmap: maps to bcm5974, good
* bcm5974: module is loaded
* /proc/bus/input/devices: module is registered
Couldn't find synaptics properties. No synaptics driver loaded?

```

Any idea how to get this working?

---

### Post by tomsecret on 2011-03-12
Hi, sorry for reviving an old thread, but it's still relevant for me :) I'm about to buy a macbookpro7,1, and have been reading this entire thread and the community wiki. Are there any problems left when using macbookpro7,1 and Ubuntu (with gnome) 10.10 or 11.04? I have three questions:

1. Does the video bug ([https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/681465](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/681465)) affect all machines?

2. What kind of battery life do you have in your everyday use? 

3. Also are there any other serious bugs when using Ubuntu on this machine?

Thanks for your time! :)

---

### Post by vickoxy on 2011-03-21
> **scullez said:**
> Don't forget to run update-grub after editing /etc/default/grub. Have you did that?

You have to install and configure pommed using this wiki: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

Hi,
i have same problems-still can not get the LCD Brightness setup. I posted my question alo here:
> i,
i still have brightness adjustment problems (F1-F2). I have MacBook Pro 7.1 and Ubuntu 10.04 64bit. I installed Ubuntu following this guide:
[https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)
After i made for the first time: 
Code:
sudo apt-get remove pommed
sudo apt-get install git-core libdbus-1-dev libconfuse-dev libaudiofile-dev libasound-dev libpci-dev libdbus-glib-1-dev libglade2-dev libgtk2.0-dev libx11-dev libxext-dev libxpm-dev
git clone git://git.debian.org/git/pommed/pommed.git
cd pommed
make
I had keyboard and screen light working. But after few restarts, and - i think - after i activated nvidia drivers, i can´t set up brightness any more-it stays always on the 100%.

I followed instructions on this forum, but nothing helps me. Anyone knows how to fix this?

but nothing...

Is there some easy fix for this issue?

---

### Post by sciurus on 2011-04-29
Does anyone know if the problems and workarounds for the MacBookPro7,1 running Ubuntu 10.10 documented at [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick) have changed at all for Ubuntu 11.04?

---

### Post by luismacb on 2011-04-30
Upgraded to 11.04 on macbook pro 7,1.
Sound doesn't work. It was working on ubuntu 10.10, but not now. I run alsamixer and everything is unmuted, and at 100% volume. However, there is no front speaker control.
My Nvidia mcp89 is recognized and every looks working in gnome-volume-control, but no sound.

---

### Post by watgrad on 2011-05-01
This is what I did to get sound working in Natty- 
[https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Sound](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Sound)

---

### Post by watgrad on 2011-05-01
> **sciurus said:**
> Does anyone know if the problems and workarounds for the MacBookPro7,1 running Ubuntu 10.10 documented at [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick) have changed at all for Ubuntu 11.04?

I was able to use the maverick directions to get a clean install of natty working. I did have some trouble with the keys for display brightness at first - but all works well now.

---

### Post by luismacb on 2011-05-02
I did that in 10.10, and after upgrade, sound alsa-base.conf remains with that line. That's not the problem.
It seems a bad config of pulseaudio, or maybe alsa, beacause the nvidia card is recognized and all unmutted but no sound at all.

---

### Post by luismacb on 2011-05-02
I can't believe it!!

I found the solution. It was all the Mactel PPA, this is a big mistake, this should be warned!! Those untrusted ppas.... ](*,)

So, simply uninstall snd-hda-dkms with Synaptics and reboot!

Via: [http://ubuntuforums.org/showpost.php?p=10747611&postcount=307](http://ubuntuforums.org/showpost.php?p=10747611&postcount=307)

---

### Post by vickoxy on 2011-05-31
How does Ubuntu 11.04 work on Macbook? I have 10.10 and waking time from suspend/hibernation is not impressive, i have some freezing issues at flash sites and it just doesn´t work as smooth as with thinkpads...

---

