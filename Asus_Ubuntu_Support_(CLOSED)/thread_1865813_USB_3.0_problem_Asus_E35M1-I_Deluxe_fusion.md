---
title: "USB 3.0 problem Asus E35M1-I Deluxe fusion"
date: 2011-10-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by knorrhane on 2011-10-20
Hello!

I can't get my 2 TB WD MyBook Essential to operate at USB 3.0 speeds on my Asus E35M1-I Deluxe motherboard. Ubuntu 11.10 recognize it as a "high speed USB device" in kern.log and report 480 Mbps in disk utility. The kern.log has some warnings though:

```
Oct 20 19:50:46 LiteByte kernel: [21096.868063] usb 8-2: new high speed USB device number 3 using xhci_hcd
Oct 20 19:50:46 LiteByte kernel: [21096.885767] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.886134] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.886510] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.886884] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.888035] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.888641] xhci_hcd 0000:04:00.0: WARN: short transfer on control ep
Oct 20 19:50:46 LiteByte kernel: [21096.904447] scsi9 : usb-storage 8-2:1.0
Oct 20 19:50:47 LiteByte kernel: [21097.910237] scsi 9:0:0:0: Direct-Access     WD       My Book 1140     1003 PQ: 0 ANSI: 6
Oct 20 19:50:47 LiteByte kernel: [21097.910461] scsi 9:0:0:1: Enclosure         WD       SES Device       1003 PQ: 0 ANSI: 6
Oct 20 19:50:47 LiteByte kernel: [21098.044478] sd 9:0:0:0: Attached scsi generic sg2 type 0
Oct 20 19:50:47 LiteByte kernel: [21098.044629] ses 9:0:0:1: Attached Enclosure device
Oct 20 19:50:47 LiteByte kernel: [21098.044735] ses 9:0:0:1: Attached scsi generic sg3 type 13
Oct 20 19:50:47 LiteByte kernel: [21098.046739] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.047619] sd 9:0:0:0: [sdc] 3906963456 512-byte logical blocks: (2.00 TB/1.81 TiB)
Oct 20 19:50:47 LiteByte kernel: [21098.047731] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.048643] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.049973] sd 9:0:0:0: [sdc] Write Protect is off
Oct 20 19:50:47 LiteByte kernel: [21098.049983] sd 9:0:0:0: [sdc] Mode Sense: 47 00 10 08
Oct 20 19:50:47 LiteByte kernel: [21098.050274] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.051764] sd 9:0:0:0: [sdc] No Caching mode page present
Oct 20 19:50:47 LiteByte kernel: [21098.051780] sd 9:0:0:0: [sdc] Assuming drive cache: write through
Oct 20 19:50:47 LiteByte kernel: [21098.052516] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.054518] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.055246] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.057177] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:47 LiteByte kernel: [21098.058254] sd 9:0:0:0: [sdc] No Caching mode page present
Oct 20 19:50:47 LiteByte kernel: [21098.058264] sd 9:0:0:0: [sdc] Assuming drive cache: write through
Oct 20 19:50:55 LiteByte kernel: [21106.106664] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:55 LiteByte kernel: [21106.109120] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:57 LiteByte kernel: [21108.126695] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:57 LiteByte kernel: [21108.127257] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:59 LiteByte kernel: [21110.146739] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:50:59 LiteByte kernel: [21110.147243] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:00 LiteByte kernel: [21111.238693]  sdc: sdc1
Oct 20 19:51:00 LiteByte kernel: [21111.239461] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:00 LiteByte kernel: [21111.241190] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:00 LiteByte kernel: [21111.241940] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:00 LiteByte kernel: [21111.242861] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:00 LiteByte kernel: [21111.243284] sd 9:0:0:0: [sdc] No Caching mode page present
Oct 20 19:51:00 LiteByte kernel: [21111.243291] sd 9:0:0:0: [sdc] Assuming drive cache: write through
Oct 20 19:51:00 LiteByte kernel: [21111.243296] sd 9:0:0:0: [sdc] Attached SCSI disk
Oct 20 19:51:00 LiteByte kernel: [21111.243414] xhci_hcd 0000:04:00.0: WARN: Stalled endpoint
Oct 20 19:51:01 LiteByte kernel: [21112.168108] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
```

lspci shows the following:

```
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

So I'm guessing the kernel recognizes the USB 3.0 controller but my hard drive still doesn't get recognized as an USB 3.0 device and I'm only getting about 30-50 Mb/s. Any ideas?

Thanks!

---

### Post by m.bluemle on 2012-01-09
i´ve the same hd and the same motherboard and in my case xubuntu 11.10 didn´t even detect or mount the drive!

it seems like there are many users have problems with usb 3.0!

has anyone a solution?

---

### Post by adrien214 on 2012-01-18
did you try with kernel options

```
pci=nomsi, noaer
```

---

### Post by knorrhane on 2012-02-03
A little update on this issue. It doesn't seem to be a problem with Ubuntu as much as the mobo. Using Windows 7 the USB 3 controller will only work on some reboots, mostly the ports are dead.

I'm currently trying with BIOS and firmware update for the USB 3.0 controller, I'll report back on how this might turn out.

As for this:

> **adrien214 said:**
> did you try with kernel options

```
pci=nomsi, noaer
```

I'm not sure how this works as I'm not familiar with customized kernels and don't what it'll do. Might try it if all else fails :)

---

### Post by knorrhane on 2012-02-03
I found an USB 3.0 renesas driver for Windows 7 which I downloaded and it allowed me to turn off power saving. This fixes the issue with the USB ports not working at all sometimes. I still only get 480 Mbps.

I'm giving up for now.

---

### Post by knorrhane on 2012-02-04
Solved!

I updated the BIOS to 1305 and Ubuntu now recognize my WD My Book Essential as a USB 3.0 drive and it shows 705 MB/s in disk utility.

---

