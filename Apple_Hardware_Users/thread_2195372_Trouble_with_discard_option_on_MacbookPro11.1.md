---
title: "Trouble with discard option on MacbookPro11.1"
date: 2013-12-23
forum: Apple Hardware Users
---

### Post by LonelyStar on 2013-12-23
Hey,

I got a new MacBookPro (13,3 inch screen, retina display, MacBookPro11.1) and have touble with the ssd. I enabled the "discard" option in /etc/fstab. Now, from time to time the screen freezes for about 20 seconds. dmesg gives me:
```

[   11.860569] ERROR @wl_inform_single_bss : cfg80211_inform_bss_frame error
[   98.888329] ata1.00: exception Emask 0x0 SAct 0x1fff SErr 0x0 action 0x6 frozen
[   98.888334] ata1.00: failed command: READ FPDMA QUEUED
[   98.888338] ata1.00: cmd 60/48:00:f8:26:ef/00:00:17:00:00/40 tag 0 ncq 36864 in
[   98.888338]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[   98.888340] ata1.00: status: { DRDY }
[   98.888342] ata1.00: failed command: READ FPDMA QUEUED
[   98.888345] ata1.00: cmd 60/08:08:50:27:ef/00:00:17:00:00/40 tag 1 ncq 4096 in
[   98.888345]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888346] ata1.00: status: { DRDY }
[   98.888348] ata1.00: failed command: READ FPDMA QUEUED
[   98.888351] ata1.00: cmd 60/30:10:c8:27:ef/00:00:17:00:00/40 tag 2 ncq 24576 in
[   98.888351]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888352] ata1.00: status: { DRDY }
[   98.888353] ata1.00: failed command: READ FPDMA QUEUED
[   98.888356] ata1.00: cmd 60/08:18:58:49:ef/00:00:17:00:00/40 tag 3 ncq 4096 in
[   98.888356]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888358] ata1.00: status: { DRDY }
[   98.888359] ata1.00: failed command: READ FPDMA QUEUED
[   98.888362] ata1.00: cmd 60/08:20:80:83:18/00:00:1b:00:00/40 tag 4 ncq 4096 in
[   98.888362]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888363] ata1.00: status: { DRDY }
[   98.888365] ata1.00: failed command: READ FPDMA QUEUED
[   98.888367] ata1.00: cmd 60/08:28:c0:8e:d8/00:00:16:00:00/40 tag 5 ncq 4096 in
[   98.888367]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888369] ata1.00: status: { DRDY }
[   98.888370] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888373] ata1.00: cmd 61/08:30:10:16:a0/00:00:17:00:00/40 tag 6 ncq 4096 out
[   98.888373]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888374] ata1.00: status: { DRDY }
[   98.888376] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888378] ata1.00: cmd 61/08:38:38:2a:1e/00:00:10:00:00/40 tag 7 ncq 4096 out
[   98.888378]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888380] ata1.00: status: { DRDY }
[   98.888381] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888384] ata1.00: cmd 61/30:40:10:90:9b/00:00:15:00:00/40 tag 8 ncq 24576 out
[   98.888384]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888385] ata1.00: status: { DRDY }
[   98.888387] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888389] ata1.00: cmd 61/08:48:b8:b9:1b/00:00:17:00:00/40 tag 9 ncq 4096 out
[   98.888389]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888391] ata1.00: status: { DRDY }
[   98.888392] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888395] ata1.00: cmd 61/08:50:50:80:dd/00:00:15:00:00/40 tag 10 ncq 4096 out
[   98.888395]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888396] ata1.00: status: { DRDY }
[   98.888398] ata1.00: failed command: WRITE FPDMA QUEUED
[   98.888400] ata1.00: cmd 61/08:58:30:a0:e2/00:00:0f:00:00/40 tag 11 ncq 4096 out
[   98.888400]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888402] ata1.00: status: { DRDY }
[   98.888403] ata1.00: failed command: READ FPDMA QUEUED
[   98.888406] ata1.00: cmd 60/20:60:80:dd:ea/00:00:14:00:00/40 tag 12 ncq 16384 in
[   98.888406]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   98.888407] ata1.00: status: { DRDY }
[   98.888411] ata1: hard resetting link
[   99.216264] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   99.216561] ata1.00: unexpected _GTF length (8)
[   99.217171] ata1.00: unexpected _GTF length (8)
[   99.217347] ata1.00: configured for UDMA/133
[   99.217368] ata1.00: device reported invalid CHS sector 0
[   99.217370] ata1.00: device reported invalid CHS sector 0
[   99.217371] ata1.00: device reported invalid CHS sector 0
[   99.217373] ata1.00: device reported invalid CHS sector 0
[   99.217385] ata1.00: device reported invalid CHS sector 0
[   99.217386] ata1.00: device reported invalid CHS sector 0
[   99.217387] ata1.00: device reported invalid CHS sector 0
[   99.217389] ata1.00: device reported invalid CHS sector 0
[   99.217390] ata1.00: device reported invalid CHS sector 0
[   99.217391] ata1.00: device reported invalid CHS sector 0
[   99.217393] ata1.00: device reported invalid CHS sector 0
[   99.217394] ata1.00: device reported invalid CHS sector 0
[   99.217396] ata1.00: device reported invalid CHS sector 0
[   99.217405] ata1: EH complete

```

I read a lot about similar errors on the Internet, but nothing that helped ...

Thanks!
Nathan

---

