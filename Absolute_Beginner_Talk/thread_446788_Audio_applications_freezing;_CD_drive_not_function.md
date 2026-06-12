---
title: "Audio applications freezing; CD drive not functioning correctly"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by kvk on 2007-05-17
I am having difficulties playing/ripping CDs. Any application I use (Sound Juicer, Amarok, Rhythmbox) freezes when directed to access the CD drive and needs a force quit, while the CD drive limps along starting and stopping repeatedly. Once or twice Sound Juicer has spontaneously opened up and begun to rip tracks to the music directory, but immediately begins to slow to a crawl and then halt. According to Keir Thomas' book "Ubuntu Linux", DMA is enabled by default in 6.06, so that's most likely not the issue. 

The box is a four year-old Dell with a CD/DVD drive, but no RW capability. The fact that SJ has been able to rip tracks tells me that Ubuntu can detect the drive, but I'm not sure where else to look for a solution.

Thanks so much!!!

---

### Post by trent dillman on 2007-05-18
...

---

### Post by kvk on 2007-05-18
No; I'm fairly limited, hardware-wise. But I just reinstalled Ubuntu again; I had a dual partition with XP and thought that might be the problem so I wiped it all and just have Ubuntu on the drive now. It read the Ubuntu CD with no problem, and XP didn't have any trouble reading CD/DVDs either.

But after reinstalling and downloading all updates and such, the problem still exists. :(

Dang!

---

### Post by trent dillman on 2007-05-18
...

---

### Post by kvk on 2007-05-18
Hmmm..okay; I'll check dmesg.

Um...what is that and how do I check it? Is that accessed through the terminal?

---

### Post by kvk on 2007-05-18
Okay- never mind! I've got the log- I'll go through it and see what I can find. Thanks!

---

### Post by kvk on 2007-05-19
Interesting.

Sound Juicer came out of the blue and functioned correctly- ripping CD tracks to the music directory. When a second CD was loaded, it did what it has been doing.

The dmesg reads:

[17179808.912000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[17179808.912000] ide: failed opcode was: unknown
[17179808.912000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[17201211.224000] [drm:r128_cce_depth] *ERROR* r128_cce_depth called without loc k held
[17201211.224000] [drm:r128_cce_idle] *ERROR* r128_cce_idle called without lock held

...over and over.

When it did function correctly, it reads:

[17179573.876000] Probing IDE interface ide0...
[17179574.164000] hda: IC35L080AVVA07-0, ATA DISK drive
[17179574.836000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.848000] Probing IDE interface ide1...
[17179575.584000] hdc: LITEON DVD-ROM LTD163, ATAPI CD/DVD-ROM drive
[17179575.920000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.928000] hda: max request size: 128KiB
[17179575.940000] hda: 156250000 sectors (80000 MB) w/1863KiB Cache, CHS=65535/1 6/63, UDMA(100)
[17179575.940000] hda: cache flushes supported
[17179575.940000]  hda: hda1 hda2 < hda5 >
[17179575.984000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179575.984000] Uniform CD-ROM driver Revision: 3.20
[17179576.280000] usbcore: registered new driver usbfs
[17179576.280000] usbcore: registered new driver hub
[17179576.284000] USB Universal Host Controller Interface driver v2.3
[17179576.284000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177

and continued on to read the CD correctly,

Where can I look to trace the error codes to a source problem so I can fix it?

---

