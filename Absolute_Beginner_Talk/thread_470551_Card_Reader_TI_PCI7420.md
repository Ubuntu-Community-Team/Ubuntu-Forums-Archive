---
title: "Card Reader TI PCI7420"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-06-11
Hi,

I'm reading this post:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923)

but I can't get a working card reader on feisty. That's my 'lspci':

00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller

uname -a : 

2.6.20-16-generic

my notebook is an acer 1524wlmi (32 bit system)

have you any idea to solve this problem?

Thanks,
alex

---

### Post by Pragmatist on 2007-06-12
If it is a USB card reader, try this:  First, while the reader is unplugged, type this in a terminal:
```
tail -f /var/log/messages
```

Now plug in the device and watch for messages in the terminal.  Post those here.    Also, make sure to put a media card into the reader and watch for messages.

---

### Post by slamdunk on 2007-06-12
Jun 12 09:52:26 mybox kernel: [ 3354.328000] pccard: PCMCIA card inserted into slot 0
Jun 12 09:52:26 mybox kernel: [ 3354.328000] pcmcia: registering new device pcmcia0.0
Jun 12 09:52:26 mybox kernel: [ 3354.368000] ata2: PATA max PIO0 cmd 0x00010100 ctl 0x0001010e bmdma 0x00000000 irq 3
Jun 12 09:52:26 mybox kernel: [ 3354.368000] scsi1 : pata_pcmcia
Jun 12 09:52:26 mybox kernel: [ 3354.556000] ata2.00: CFA: Memory Card Adapter, 20030623, max PIO1
Jun 12 09:52:26 mybox kernel: [ 3354.556000] ata2.00: 62720 sectors, multi 0: LBA 
Jun 12 09:52:26 mybox kernel: [ 3354.556000] ata2.01: CFA: Memory Card Adapter, 20030623, max PIO1
Jun 12 09:52:26 mybox kernel: [ 3354.556000] ata2.01: 62720 sectors, multi 0: LBA 
Jun 12 09:52:26 mybox kernel: [ 3354.564000] ata2.00: configured for PIO0
Jun 12 09:52:26 mybox kernel: [ 3354.572000] ata2.01: configured for PIO0
Jun 12 09:52:26 mybox kernel: [ 3354.572000] scsi 1:0:0:0: Direct-Access     ATA      Memory Card Adap 2003 PQ: 0 ANSI: 5
Jun 12 09:52:26 mybox kernel: [ 3354.572000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:26 mybox kernel: [ 3354.572000] sda: Write Protect is off
Jun 12 09:52:26 mybox kernel: [ 3354.576000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:26 mybox kernel: [ 3354.576000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:26 mybox kernel: [ 3354.576000] sda: Write Protect is off
Jun 12 09:52:26 mybox kernel: [ 3354.576000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:26 mybox kernel: [ 3354.576000]  sda: sda1
Jun 12 09:52:26 mybox kernel: [ 3354.580000] sd 1:0:0:0: Attached scsi removable disk sda
Jun 12 09:52:26 mybox kernel: [ 3354.580000] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jun 12 09:52:26 mybox kernel: [ 3354.584000] scsi 1:0:1:0: Direct-Access     ATA      Memory Card Adap 2003 PQ: 0 ANSI: 5
Jun 12 09:52:26 mybox kernel: [ 3354.584000] SCSI device sdb: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:26 mybox kernel: [ 3354.584000] sdb: Write Protect is off
Jun 12 09:52:26 mybox kernel: [ 3354.588000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:26 mybox kernel: [ 3354.588000] SCSI device sdb: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:26 mybox kernel: [ 3354.588000] sdb: Write Protect is off
Jun 12 09:52:26 mybox kernel: [ 3354.588000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:27 mybox kernel: [ 3354.588000]  sdb:<3>ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 12 09:52:27 mybox kernel: [ 3355.704000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:27 mybox kernel: [ 3355.720000] ata2.00: configured for PIO0
Jun 12 09:52:27 mybox kernel: [ 3355.728000] ata2.01: configured for PIO0
Jun 12 09:52:27 mybox kernel: [ 3355.728000] ata2: EH complete
Jun 12 09:52:28 mybox kernel: [ 3356.844000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:28 mybox kernel: [ 3356.860000] ata2.00: configured for PIO0
Jun 12 09:52:28 mybox kernel: [ 3356.868000] ata2.01: configured for PIO0
Jun 12 09:52:28 mybox kernel: [ 3356.868000] ata2: EH complete
Jun 12 09:52:28 mybox kernel: [ 3356.868000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:29 mybox kernel: [ 3357.984000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:29 mybox kernel: [ 3358.000000] ata2.00: configured for PIO0
Jun 12 09:52:29 mybox kernel: [ 3358.008000] ata2.01: configured for PIO0
Jun 12 09:52:29 mybox kernel: [ 3358.008000] ata2: EH complete
Jun 12 09:52:29 mybox kernel: [ 3358.008000] sda: Write Protect is off
Jun 12 09:52:30 mybox kernel: [ 3359.124000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:30 mybox kernel: [ 3359.140000] ata2.00: configured for PIO0
Jun 12 09:52:30 mybox kernel: [ 3359.148000] ata2.01: configured for PIO0
Jun 12 09:52:30 mybox kernel: [ 3359.148000] ata2: EH complete
Jun 12 09:52:31 mybox kernel: [ 3360.264000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:31 mybox kernel: [ 3360.280000] ata2.00: configured for PIO0
Jun 12 09:52:31 mybox kernel: [ 3360.288000] ata2.01: configured for PIO0
Jun 12 09:52:31 mybox kernel: [ 3360.288000] ata2: EH complete
Jun 12 09:52:31 mybox kernel: [ 3360.288000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:33 mybox kernel: [ 3361.404000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:33 mybox kernel: [ 3361.420000] ata2.00: configured for PIO0
Jun 12 09:52:33 mybox kernel: [ 3361.428000] ata2.01: configured for PIO0
Jun 12 09:52:33 mybox kernel: [ 3361.428000] sd 1:0:1:0: SCSI error: return code = 0x08000002
Jun 12 09:52:33 mybox kernel: [ 3361.428000] sdb: Current [descriptor]: sense key: Medium Error
Jun 12 09:52:33 mybox kernel: [ 3361.428000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 12 09:52:33 mybox kernel: [ 3361.428000] Descriptor sense data with sense descriptors (in hex):
Jun 12 09:52:33 mybox kernel: [ 3361.428000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 12 09:52:33 mybox kernel: [ 3361.428000]         00 00 00 00 
Jun 12 09:52:33 mybox kernel: [ 3361.428000] end_request: I/O error, dev sdb, sector 0
Jun 12 09:52:33 mybox kernel: [ 3361.428000] printk: 28 messages suppressed.
Jun 12 09:52:33 mybox kernel: [ 3361.428000] ata2: EH complete
Jun 12 09:52:34 mybox kernel: [ 3362.544000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:34 mybox kernel: [ 3362.560000] ata2.00: configured for PIO0
Jun 12 09:52:34 mybox kernel: [ 3362.568000] ata2.01: configured for PIO0
Jun 12 09:52:34 mybox kernel: [ 3362.568000] ata2: EH complete
Jun 12 09:52:34 mybox kernel: [ 3362.568000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:35 mybox kernel: [ 3363.684000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:35 mybox kernel: [ 3363.700000] ata2.00: configured for PIO0
Jun 12 09:52:35 mybox kernel: [ 3363.708000] ata2.01: configured for PIO0
Jun 12 09:52:35 mybox kernel: [ 3363.708000] ata2: EH complete
Jun 12 09:52:35 mybox kernel: [ 3363.708000] sda: Write Protect is off
Jun 12 09:52:36 mybox kernel: [ 3364.824000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:36 mybox kernel: [ 3364.840000] ata2.00: configured for PIO0
Jun 12 09:52:36 mybox kernel: [ 3364.848000] ata2.01: configured for PIO0
Jun 12 09:52:36 mybox kernel: [ 3364.848000] ata2: EH complete
Jun 12 09:52:37 mybox kernel: [ 3365.964000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:37 mybox kernel: [ 3365.980000] ata2.00: configured for PIO0
Jun 12 09:52:37 mybox kernel: [ 3365.988000] ata2.01: configured for PIO0
Jun 12 09:52:37 mybox kernel: [ 3365.988000] ata2: EH complete
Jun 12 09:52:37 mybox kernel: [ 3365.988000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:38 mybox kernel: [ 3367.104000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:38 mybox kernel: [ 3367.120000] ata2.00: configured for PIO0
Jun 12 09:52:38 mybox kernel: [ 3367.128000] ata2.01: configured for PIO0
Jun 12 09:52:38 mybox kernel: [ 3367.128000] ata2: EH complete
Jun 12 09:52:39 mybox kernel: [ 3368.244000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:39 mybox kernel: [ 3368.260000] ata2.00: configured for PIO0
Jun 12 09:52:39 mybox kernel: [ 3368.268000] ata2.01: configured for PIO0
Jun 12 09:52:39 mybox kernel: [ 3368.268000] sd 1:0:1:0: SCSI error: return code = 0x08000002
Jun 12 09:52:39 mybox kernel: [ 3368.268000] sdb: Current [descriptor]: sense key: Medium Error
Jun 12 09:52:39 mybox kernel: [ 3368.268000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 12 09:52:39 mybox kernel: [ 3368.268000] Descriptor sense data with sense descriptors (in hex):
Jun 12 09:52:39 mybox kernel: [ 3368.268000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 12 09:52:39 mybox kernel: [ 3368.268000]         00 00 00 00 
Jun 12 09:52:39 mybox kernel: [ 3368.268000] end_request: I/O error, dev sdb, sector 0
Jun 12 09:52:39 mybox kernel: [ 3368.268000] ata2: EH complete
Jun 12 09:52:39 mybox kernel: [ 3368.272000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:41 mybox kernel: [ 3369.384000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:41 mybox kernel: [ 3369.400000] ata2.00: configured for PIO0
Jun 12 09:52:41 mybox kernel: [ 3369.408000] ata2.01: configured for PIO0
Jun 12 09:52:41 mybox kernel: [ 3369.408000] ata2: EH complete
Jun 12 09:52:41 mybox kernel: [ 3369.408000] sda: Write Protect is off
Jun 12 09:52:42 mybox kernel: [ 3370.524000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:42 mybox kernel: [ 3370.540000] ata2.00: configured for PIO0
Jun 12 09:52:42 mybox kernel: [ 3370.548000] ata2.01: configured for PIO0
Jun 12 09:52:42 mybox kernel: [ 3370.548000] ata2: EH complete
Jun 12 09:52:43 mybox kernel: [ 3371.664000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:43 mybox kernel: [ 3371.680000] ata2.00: configured for PIO0
Jun 12 09:52:43 mybox kernel: [ 3371.688000] ata2.01: configured for PIO0
Jun 12 09:52:43 mybox kernel: [ 3371.688000] ata2: EH complete
Jun 12 09:52:43 mybox kernel: [ 3371.688000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:44 mybox kernel: [ 3372.804000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:44 mybox kernel: [ 3372.820000] ata2.00: configured for PIO0
Jun 12 09:52:44 mybox kernel: [ 3372.828000] ata2.01: configured for PIO0
Jun 12 09:52:44 mybox kernel: [ 3372.828000] ata2: EH complete
Jun 12 09:52:45 mybox kernel: [ 3373.944000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:45 mybox kernel: [ 3373.960000] ata2.00: configured for PIO0
Jun 12 09:52:45 mybox kernel: [ 3373.968000] ata2.01: configured for PIO0
Jun 12 09:52:45 mybox kernel: [ 3373.968000] ata2: EH complete
Jun 12 09:52:45 mybox kernel: [ 3373.968000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:46 mybox kernel: [ 3375.084000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:46 mybox kernel: [ 3375.100000] ata2.00: configured for PIO0
Jun 12 09:52:46 mybox kernel: [ 3375.108000] ata2.01: configured for PIO0
Jun 12 09:52:46 mybox kernel: [ 3375.108000] sd 1:0:1:0: SCSI error: return code = 0x08000002
Jun 12 09:52:46 mybox kernel: [ 3375.108000] sdb: Current [descriptor]: sense key: Medium Error
Jun 12 09:52:46 mybox kernel: [ 3375.108000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 12 09:52:46 mybox kernel: [ 3375.108000] Descriptor sense data with sense descriptors (in hex):
Jun 12 09:52:46 mybox kernel: [ 3375.108000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 12 09:52:46 mybox kernel: [ 3375.108000]         00 00 00 00 
Jun 12 09:52:46 mybox kernel: [ 3375.108000] end_request: I/O error, dev sdb, sector 0
Jun 12 09:52:46 mybox kernel: [ 3375.108000] ata2: EH complete
Jun 12 09:52:46 mybox kernel: [ 3375.108000] sda: Write Protect is off
Jun 12 09:52:47 mybox kernel: [ 3376.224000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:47 mybox kernel: [ 3376.240000] ata2.00: configured for PIO0
Jun 12 09:52:47 mybox kernel: [ 3376.248000] ata2.01: configured for PIO0
Jun 12 09:52:47 mybox kernel: [ 3376.248000] ata2: EH complete
Jun 12 09:52:49 mybox kernel: [ 3377.364000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:49 mybox kernel: [ 3377.380000] ata2.00: configured for PIO0
Jun 12 09:52:49 mybox kernel: [ 3377.388000] ata2.01: configured for PIO0
Jun 12 09:52:49 mybox kernel: [ 3377.388000] ata2: EH complete
Jun 12 09:52:49 mybox kernel: [ 3377.388000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:50 mybox kernel: [ 3378.504000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:50 mybox kernel: [ 3378.520000] ata2.00: configured for PIO0
Jun 12 09:52:50 mybox kernel: [ 3378.528000] ata2.01: configured for PIO0
Jun 12 09:52:50 mybox kernel: [ 3378.528000] ata2: EH complete
Jun 12 09:52:51 mybox kernel: [ 3379.644000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:51 mybox kernel: [ 3379.660000] ata2.00: configured for PIO0
Jun 12 09:52:51 mybox kernel: [ 3379.668000] ata2.01: configured for PIO0
Jun 12 09:52:51 mybox kernel: [ 3379.668000] ata2: EH complete
Jun 12 09:52:51 mybox kernel: [ 3379.668000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:52 mybox kernel: [ 3380.784000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:52 mybox kernel: [ 3380.800000] ata2.00: configured for PIO0
Jun 12 09:52:52 mybox kernel: [ 3380.808000] ata2.01: configured for PIO0
Jun 12 09:52:52 mybox kernel: [ 3380.808000] ata2: EH complete
Jun 12 09:52:52 mybox kernel: [ 3380.812000] sda: Write Protect is off
Jun 12 09:52:53 mybox kernel: [ 3381.920000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:53 mybox kernel: [ 3381.936000] ata2.00: configured for PIO0
Jun 12 09:52:53 mybox kernel: [ 3381.944000] ata2.01: configured for PIO0
Jun 12 09:52:53 mybox kernel: [ 3381.944000] sd 1:0:1:0: SCSI error: return code = 0x08000002
Jun 12 09:52:53 mybox kernel: [ 3381.944000] sdb: Current [descriptor]: sense key: Medium Error
Jun 12 09:52:53 mybox kernel: [ 3381.944000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 12 09:52:53 mybox kernel: [ 3381.944000] Descriptor sense data with sense descriptors (in hex):
Jun 12 09:52:53 mybox kernel: [ 3381.944000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 12 09:52:53 mybox kernel: [ 3381.944000]         00 00 00 00 
Jun 12 09:52:53 mybox kernel: [ 3381.944000] end_request: I/O error, dev sdb, sector 0
Jun 12 09:52:53 mybox kernel: [ 3381.944000] ata2: EH complete
Jun 12 09:52:54 mybox kernel: [ 3383.060000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:54 mybox kernel: [ 3383.076000] ata2.00: configured for PIO0
Jun 12 09:52:54 mybox kernel: [ 3383.084000] ata2.01: configured for PIO0
Jun 12 09:52:54 mybox kernel: [ 3383.084000] ata2: EH complete
Jun 12 09:52:54 mybox kernel: [ 3383.084000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:52:55 mybox kernel: [ 3384.200000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:55 mybox kernel: [ 3384.216000] ata2.00: configured for PIO0
Jun 12 09:52:55 mybox kernel: [ 3384.224000] ata2.01: configured for PIO0
Jun 12 09:52:55 mybox kernel: [ 3384.224000] ata2: EH complete
Jun 12 09:52:56 mybox kernel: [ 3385.340000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:56 mybox kernel: [ 3385.356000] ata2.00: configured for PIO0
Jun 12 09:52:57 mybox kernel: [ 3385.364000] ata2.01: configured for PIO0
Jun 12 09:52:57 mybox kernel: [ 3385.364000] ata2: EH complete
Jun 12 09:52:57 mybox kernel: [ 3385.364000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:52:58 mybox kernel: [ 3386.480000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:58 mybox kernel: [ 3386.496000] ata2.00: configured for PIO0
Jun 12 09:52:58 mybox kernel: [ 3386.504000] ata2.01: configured for PIO0
Jun 12 09:52:58 mybox kernel: [ 3386.504000] ata2: EH complete
Jun 12 09:52:58 mybox kernel: [ 3386.504000] sda: Write Protect is off
Jun 12 09:52:59 mybox kernel: [ 3387.620000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:52:59 mybox kernel: [ 3387.636000] ata2.00: configured for PIO0
Jun 12 09:52:59 mybox kernel: [ 3387.644000] ata2.01: configured for PIO0
Jun 12 09:52:59 mybox kernel: [ 3387.644000] ata2: EH complete
Jun 12 09:53:00 mybox kernel: [ 3388.760000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:53:00 mybox kernel: [ 3388.776000] ata2.00: configured for PIO0
Jun 12 09:53:00 mybox kernel: [ 3388.784000] ata2.01: configured for PIO0
Jun 12 09:53:00 mybox kernel: [ 3388.784000] sd 1:0:1:0: SCSI error: return code = 0x08000002
Jun 12 09:53:00 mybox kernel: [ 3388.784000] sdb: Current [descriptor]: sense key: Medium Error
Jun 12 09:53:00 mybox kernel: [ 3388.784000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 12 09:53:00 mybox kernel: [ 3388.784000] Descriptor sense data with sense descriptors (in hex):
Jun 12 09:53:00 mybox kernel: [ 3388.784000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 12 09:53:00 mybox kernel: [ 3388.784000]         00 00 00 00 
Jun 12 09:53:00 mybox kernel: [ 3388.784000] end_request: I/O error, dev sdb, sector 0
Jun 12 09:53:00 mybox kernel: [ 3388.784000] ata2: EH complete
Jun 12 09:53:00 mybox kernel: [ 3388.788000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:53:01 mybox kernel: [ 3389.900000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:53:01 mybox kernel: [ 3389.916000] ata2.00: configured for PIO0
Jun 12 09:53:01 mybox kernel: [ 3389.924000] ata2.01: configured for PIO0
Jun 12 09:53:01 mybox kernel: [ 3389.924000] ata2: EH complete
Jun 12 09:53:02 mybox kernel: [ 3391.040000]          res 51/40:08:00:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
Jun 12 09:53:02 mybox kernel: [ 3391.056000] ata2.00: configured for PIO0
Jun 12 09:53:02 mybox kernel: [ 3391.064000] ata2.01: configured for PIO0
Jun 12 09:53:02 mybox kernel: [ 3391.064000] ata2: EH complete
Jun 12 09:53:02 mybox kernel: [ 3391.064000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
........
sd 1:0:1:0: Attached scsi removable disk sdb
Jun 12 09:54:02 mybox kernel: [ 3450.532000] sd 1:0:1:0: Attached scsi generic sg1 type 0
Jun 12 09:54:02 mybox kernel: [ 3450.536000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:54:02 mybox kernel: [ 3450.540000] SCSI device sdb: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:54:02 mybox kernel: [ 3450.540000] sdb: Write Protect is off
Jun 12 09:54:02 mybox kernel: [ 3450.544000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:54:02 mybox kernel: [ 3450.544000] SCSI device sda: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:54:02 mybox kernel: [ 3450.548000] sda: Write Protect is off
Jun 12 09:54:02 mybox kernel: [ 3450.552000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:54:02 mybox kernel: [ 3450.556000] SCSI device sdb: 62720 512-byte hdwr sectors (32 MB)
Jun 12 09:54:02 mybox kernel: [ 3450.556000] sdb: Write Protect is off
Jun 12 09:54:02 mybox kernel: [ 3450.560000] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 12 09:54:32 mybox kernel: [ 3480.940000]          res 40/00:08:00:00:00/00:00:00:00:00/f0 Emask 0x4 (timeout)

Thanks,
Alex

---

### Post by Pragmatist on 2007-06-12
You got all of that output with the "tail -f /var/log/messages" command?  Are you sure you included the "-f" ?

Also, what type of media card did you insert, and what is its size?

After you insert the media, type this and post the output here:
```
mount
```

---

### Post by slamdunk on 2007-06-12
yes i have included in "pipe" -f (I just cut it)

32MB I suppose MMC (I'm not expert and I don't read any mark on card, however with debian works)

# mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda1 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)

Alex

---

### Post by Pragmatist on 2007-06-12
After you insert the card, give output to this:
```
ls -l /dev/sd*
```

---

### Post by slamdunk on 2007-06-12
$ ls -l /dev/sd*
brw-rw---- 1 root floppy 8, 0 2007-06-12 10:36 /dev/sda

---

### Post by slamdunk on 2007-06-12
# mount /dev/sda /media/mycard
mount: /dev/sda: can't read superblock

with or without '-t vfat'

is there a solution for it?

---

### Post by Pragmatist on 2007-06-12
Have you used this card yet?  Can you access the card on another OS?  Is there anything on the card?

---

### Post by slamdunk on 2007-06-13
I cannot access to this card with another OS but I can see its content with my mobile phone

Alex

---

### Post by Pragmatist on 2007-06-13
What do you get when you type this with the card inserted:
```
sudo fdisk /dev/sda
```

---

### Post by slamdunk on 2007-06-13
after many seconds it returns:

$ sudo fdisk /dev/sda

Unable to read /dev/sda

Alex

---

### Post by Pragmatist on 2007-06-13
Sorry, accidentally posted a suggestion I already made before!  Still thinking.

---

