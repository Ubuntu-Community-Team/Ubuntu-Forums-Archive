---
title: "OWC Mercury Aura Pro Express"
date: 2012-03-26
forum: Apple Hardware Users
---

### Post by rk8102 on 2012-03-26
I have a problem with my Macbook Air (3,1) and the upgraded SSD (OWC Mercury Aura Pro Express, Sandforce 1200 controller) ... the SSD is recognized by the kernel and the device gets configured (/dev/sda) however, I can't install to it - gparted claims there are no devices. I find this in the dmesg:

```
[    5.824143] ata1.00: ATA-8: OWC Mercury Aura Pro Express SSD, 361A13F0, max UDMA/133
[    5.824148] ata1.00: 351651888 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    5.824154] ata1.00: configured for UDMA/133
[    5.993832] Write protecting the kernel read-only data: 10240k
[   36.832117] ata1: lost interrupt (Status 0x58)
[   36.832327] ata1: drained 512 bytes to clear DRQ.
[   36.832336] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   36.832342] ata1.00: failed command: IDENTIFY DEVICE
[   36.832350] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   36.832356] ata1.00: status: { DRDY }
[   36.832366] ata1: soft resetting link
[   36.996257] ata1.00: configured for UDMA/133
[   36.996279] ata1: EH complete
[  109.824094] ata1: lost interrupt (Status 0x58)
[  109.824303] ata1: drained 512 bytes to clear DRQ.
[  109.824312] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  109.824318] ata1.00: failed command: IDENTIFY DEVICE
[  109.824326] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  109.824331] ata1.00: status: { DRDY }
[  109.824342] ata1: soft resetting link
[  109.988275] ata1.00: configured for UDMA/133
[  109.988294] ata1: EH complete
[  140.896108] ata1: lost interrupt (Status 0x58)
[  140.896324] ata1: drained 512 bytes to clear DRQ.
[  140.896334] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  140.896339] ata1.00: failed command: IDENTIFY DEVICE
[  140.896347] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  140.896353] ata1.00: status: { DRDY }
[  140.896363] ata1: soft resetting link
[  141.060251] ata1.00: configured for UDMA/133
[  141.060265] ata1: EH complete
[  182.384354] [drm] nouveau 0000:02:00.0: PGRAPH - ch 2 (0x0000730000) subc 5 class 0x8697 mthd 0x16b0 data 0x00000000
[  191.840130] ata1: lost interrupt (Status 0x58)
[  191.840340] ata1: drained 512 bytes to clear DRQ.
[  191.840350] ata1.00: limiting speed to UDMA/133:PIO6
[  191.840355] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  191.840361] ata1.00: failed command: IDENTIFY DEVICE
[  191.840369] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  191.840375] ata1.00: status: { DRDY }
[  191.840386] ata1: soft resetting link
[  192.004274] ata1.00: configured for UDMA/133
[  192.004297] ata1: EH complete
[  199.808165] ata1: lost interrupt (Status 0x58)
[  199.808375] ata1: drained 512 bytes to clear DRQ.
[  199.808384] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  199.808391] ata1.00: failed command: IDENTIFY DEVICE
[  199.808399] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[  199.808405] ata1.00: status: { DRDY }
[  199.808416] ata1: soft resetting link
[  199.972268] ata1.00: configured for UDMA/133
[  199.972297] ata1: EH complete
[  215.840047] ata1: lost interrupt (Status 0x58)
[  215.840261] ata1: drained 512 bytes to clear DRQ.
[  215.840271] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  215.840277] ata1.00: failed command: IDENTIFY DEVICE
[  215.840285] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/40 tag 0 pio 512 in
[  215.840291] ata1.00: status: { DRDY }
[  215.840302] ata1: soft resetting link
[  216.004162] ata1.00: configured for UDMA/133
[  216.004186] ata1: EH complete
[  231.840099] ata1: lost interrupt (Status 0x51)
[  231.840118] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  231.840124] ata1.00: failed command: SET FEATURES
[  231.840132] ata1.00: cmd ef/05:80:00:00:00/00:00:00:00:00/40 tag 0
[  231.840138] ata1.00: status: { DRDY }
[  231.840149] ata1: soft resetting link
[  232.004208] ata1.00: configured for UDMA/133
[  232.004236] ata1: EH complete
[  247.840137] ata1: lost interrupt (Status 0x58)
[  247.840353] ata1: drained 512 bytes to clear DRQ.
[  247.840362] ata1.00: limiting speed to UDMA/33:PIO6
[  247.840368] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  247.840374] ata1.00: failed command: IDENTIFY DEVICE
[  247.840382] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/40 tag 0 pio 512 in
[  247.840388] ata1.00: status: { DRDY }
[  247.840399] ata1: soft resetting link
[  248.004205] ata1.00: configured for UDMA/133
[  248.004231] ata1: EH complete

```

Does anyone have any suggestions for this? I really want to get Linux on this laptop, 10.7 sucks and it's looking like 10.8 is going to suck even worse (if I wanted my Mac to be an iPad, I'd buy a iPad.)

thanks for any help!

Rob K.

---

### Post by rk8102 on 2012-03-26
I was able to get up and running using 11.10 EFI boot.  Using this mode, everything worked except graphics and by using 'nomodeset' and then configuring xorg.conf by hand, it's working great.

thanks -

Rob k.

---

