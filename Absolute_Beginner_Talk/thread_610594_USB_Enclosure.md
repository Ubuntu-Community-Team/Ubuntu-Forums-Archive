---
title: "USB Enclosure"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-11-12
Cheers,

I just bought a USB Enclosure for one of my Harddrive, and whenever I insert it in Ubuntu it gets 
mounted but after a few seconds (< 30 secs) it unmounts it automatically.

Any idea on why this is?  Im using Ubuntu 7.10.  Also the Harddisk is formatted as NTFS, since I am 
mainly using this on my Windows Laptop.

Thanks

---

### Post by Harpoon on 2007-11-12
I haven't seen thisparticular  problem, but one thing to do is make sure the drive jumper is set to "master."  On some usb's all sorts of strange things happen if it is set to "cable select."

---

### Post by delphiguy on 2007-11-12
thanks will try just that.  The funny thing is that it was working before, and just when I was
almost done transfering files it happened resulting in data loss, and I have to reformat the 
drive.

---

### Post by delphiguy on 2007-11-12
that did'nt fixed it.  I thought it was ok because after putting the jumper to master it worked, 
and then after a few minutes it returned to its previous behavior.

i give up, I have already lost my data, and I'm afraid that if I keep on that I may loose my 
HardDrive.

Now, im tranferrring files the slow way, through a wifi network.

---

### Post by az on 2007-11-12
System - Administration - System log (messages)

What gets logged when the drive unmounts spontaneously?  This sounds like hardware problems.

---

### Post by Harpoon on 2007-11-12
Hate to say it, but it sounds like a bad usb interface.  Experiment with changing cables first, if you have extras, and if that doesn't work hope you can return the faulty part under warranty.

---

### Post by delphiguy on 2007-11-12
> Nov 12 18:57:17 zion-desktop kernel: [ 8108.494627] sd 7:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:06:31 zion-desktop kernel: [ 8662.352760] usb 3-8: USB disconnect, address 6
Nov 12 19:10:28 zion-desktop kernel: [ 8899.422618] usb 3-7: new high speed USB device using ehci_hcd and address 7
Nov 12 19:10:32 zion-desktop kernel: [ 8903.197892] usb 3-7: new high speed USB device using ehci_hcd and address 8
Nov 12 19:10:35 zion-desktop kernel: [ 8906.017344] usb 3-7: new high speed USB device using ehci_hcd and address 9
Nov 12 19:10:36 zion-desktop kernel: [ 8906.730783] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:10:36 zion-desktop kernel: [ 8906.731026] scsi8 : SCSI emulation for USB Mass Storage devices
Nov 12 19:10:38 zion-desktop kernel: [ 8908.798920] usb 3-7: USB disconnect, address 9
Nov 12 19:10:38 zion-desktop kernel: [ 8909.068755] usb 3-7: new high speed USB device using ehci_hcd and address 10
Nov 12 19:10:38 zion-desktop kernel: [ 8909.462085] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:10:38 zion-desktop kernel: [ 8909.462327] scsi9 : SCSI emulation for USB Mass Storage devices
Nov 12 19:10:43 zion-desktop kernel: [ 8914.460342] scsi 9:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:10:43 zion-desktop kernel: [ 8914.461823] sd 9:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:10:43 zion-desktop kernel: [ 8914.462698] sd 9:0:0:0: [sde] Write Protect is off
Nov 12 19:10:43 zion-desktop kernel: [ 8914.463447] sd 9:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:10:43 zion-desktop kernel: [ 8914.464328] sd 9:0:0:0: [sde] Write Protect is off
Nov 12 19:10:43 zion-desktop kernel: [ 8914.464338]  sde: sde1
Nov 12 19:10:43 zion-desktop kernel: [ 8914.489379] sd 9:0:0:0: [sde] Attached SCSI disk
Nov 12 19:10:43 zion-desktop kernel: [ 8914.489414] sd 9:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:10:44 zion-desktop kernel: [ 8915.379791] usb 3-7: USB disconnect, address 10
Nov 12 19:10:45 zion-desktop kernel: [ 8915.651492] usb 3-7: new high speed USB device using ehci_hcd and address 11
Nov 12 19:10:45 zion-desktop kernel: [ 8916.036825] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:10:45 zion-desktop kernel: [ 8916.037075] scsi10 : SCSI emulation for USB Mass Storage devices
Nov 12 19:10:50 zion-desktop kernel: [ 8921.035085] scsi 10:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:10:50 zion-desktop kernel: [ 8921.036566] sd 10:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:10:50 zion-desktop kernel: [ 8921.037440] sd 10:0:0:0: [sde] Write Protect is off
Nov 12 19:10:50 zion-desktop kernel: [ 8921.038314] sd 10:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:10:50 zion-desktop kernel: [ 8921.039064] sd 10:0:0:0: [sde] Write Protect is off
Nov 12 19:10:50 zion-desktop kernel: [ 8921.039072]  sde: sde1
Nov 12 19:10:50 zion-desktop kernel: [ 8921.059132] sd 10:0:0:0: [sde] Attached SCSI disk
Nov 12 19:10:50 zion-desktop kernel: [ 8921.059167] sd 10:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:10:57 zion-desktop kernel: [ 8928.363055] usb 3-7: USB disconnect, address 11
Nov 12 19:10:58 zion-desktop kernel: [ 8928.616987] usb 3-7: new high speed USB device using ehci_hcd and address 12
Nov 12 19:10:58 zion-desktop kernel: [ 8929.002462] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:10:58 zion-desktop kernel: [ 8929.003287] scsi11 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:03 zion-desktop kernel: [ 8934.000594] scsi 11:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:11:03 zion-desktop kernel: [ 8934.002076] sd 11:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:03 zion-desktop kernel: [ 8934.002950] sd 11:0:0:0: [sde] Write Protect is off
Nov 12 19:11:03 zion-desktop kernel: [ 8934.003699] sd 11:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:03 zion-desktop kernel: [ 8934.004573] sd 11:0:0:0: [sde] Write Protect is off
Nov 12 19:11:03 zion-desktop kernel: [ 8934.004581]  sde: sde1
Nov 12 19:11:03 zion-desktop kernel: [ 8934.032131] sd 11:0:0:0: [sde] Attached SCSI disk
Nov 12 19:11:03 zion-desktop kernel: [ 8934.032166] sd 11:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:11:03 zion-desktop kernel: [ 8934.216551] usb 3-7: USB disconnect, address 12
Nov 12 19:11:03 zion-desktop kernel: [ 8934.216753] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.217184] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.217874] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.218277] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.219044] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.219438] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.219862] sd 11:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:03 zion-desktop kernel: [ 8934.223007] scsi 11:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:04 zion-desktop kernel: [ 8934.491850] usb 3-7: new high speed USB device using ehci_hcd and address 13
Nov 12 19:11:04 zion-desktop kernel: [ 8934.889345] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:11:04 zion-desktop kernel: [ 8934.889588] scsi12 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:08 zion-desktop kernel: [ 8938.547274] usb 3-7: USB disconnect, address 13
Nov 12 19:11:08 zion-desktop kernel: [ 8938.819009] usb 3-7: new high speed USB device using ehci_hcd and address 14
Nov 12 19:11:08 zion-desktop kernel: [ 8939.220310] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:11:08 zion-desktop kernel: [ 8939.224966] scsi13 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:11 zion-desktop kernel: [ 8941.714977] usb 3-7: USB disconnect, address 14
Nov 12 19:11:11 zion-desktop kernel: [ 8941.986398] usb 3-7: new high speed USB device using ehci_hcd and address 15
Nov 12 19:11:11 zion-desktop kernel: [ 8942.375893] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:11:11 zion-desktop kernel: [ 8942.376137] scsi14 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:12 zion-desktop kernel: [ 8943.466239] usb 3-7: USB disconnect, address 15
Nov 12 19:11:13 zion-desktop kernel: [ 8943.738061] usb 3-7: new high speed USB device using ehci_hcd and address 16
Nov 12 19:11:13 zion-desktop kernel: [ 8944.123531] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:11:13 zion-desktop kernel: [ 8944.123774] scsi15 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:18 zion-desktop kernel: [ 8949.121664] scsi 15:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:11:18 zion-desktop kernel: [ 8949.123146] sd 15:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:18 zion-desktop kernel: [ 8949.124019] sd 15:0:0:0: [sde] Write Protect is off
Nov 12 19:11:18 zion-desktop kernel: [ 8949.124769] sd 15:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:18 zion-desktop kernel: [ 8949.125644] sd 15:0:0:0: [sde] Write Protect is off
Nov 12 19:11:18 zion-desktop kernel: [ 8949.125651]  sde: sde1
Nov 12 19:11:18 zion-desktop kernel: [ 8949.153567] sd 15:0:0:0: [sde] Attached SCSI disk
Nov 12 19:11:18 zion-desktop kernel: [ 8949.153601] sd 15:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:11:29 zion-desktop kernel: [ 8959.937631] usb 3-7: USB disconnect, address 16
Nov 12 19:11:29 zion-desktop kernel: [ 8960.206884] usb 3-7: new high speed USB device using ehci_hcd and address 17
Nov 12 19:11:30 zion-desktop kernel: [ 8960.596175] usb 3-7: configuration #1 chosen from 1 choice
Nov 12 19:11:30 zion-desktop kernel: [ 8960.596417] scsi16 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:35 zion-desktop kernel: [ 8965.594429] scsi 16:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:11:35 zion-desktop kernel: [ 8965.595911] sd 16:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:35 zion-desktop kernel: [ 8965.596785] sd 16:0:0:0: [sde] Write Protect is off
Nov 12 19:11:35 zion-desktop kernel: [ 8965.597658] sd 16:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:35 zion-desktop kernel: [ 8965.598409] sd 16:0:0:0: [sde] Write Protect is off
Nov 12 19:11:35 zion-desktop kernel: [ 8965.598416]  sde: sde1
Nov 12 19:11:35 zion-desktop kernel: [ 8965.623837] sd 16:0:0:0: [sde] Attached SCSI disk
Nov 12 19:11:35 zion-desktop kernel: [ 8965.623871] sd 16:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:11:35 zion-desktop kernel: [ 8966.353703] usb 3-7: USB disconnect, address 17
Nov 12 19:11:35 zion-desktop kernel: [ 8966.357667] scsi 16:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:35 zion-desktop kernel: [ 8966.357679] printk: 42 messages suppressed.
Nov 12 19:11:35 zion-desktop kernel: [ 8966.357833] scsi 16:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:11:38 zion-desktop kernel: [ 8968.849210] usb 3-8: new high speed USB device using ehci_hcd and address 18
Nov 12 19:11:39 zion-desktop kernel: [ 8969.637056] usb 3-8: new high speed USB device using ehci_hcd and address 19
Nov 12 19:11:39 zion-desktop kernel: [ 8970.030379] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:11:39 zion-desktop kernel: [ 8970.030619] scsi17 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:42 zion-desktop kernel: [ 8973.087177] usb 3-8: USB disconnect, address 19
Nov 12 19:11:42 zion-desktop kernel: [ 8973.356347] usb 3-8: new high speed USB device using ehci_hcd and address 20
Nov 12 19:11:43 zion-desktop kernel: [ 8973.741845] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:11:43 zion-desktop kernel: [ 8973.742657] scsi18 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:48 zion-desktop kernel: [ 8978.739977] scsi 18:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:11:48 zion-desktop kernel: [ 8978.741458] sd 18:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:48 zion-desktop kernel: [ 8978.742333] sd 18:0:0:0: [sde] Write Protect is off
Nov 12 19:11:48 zion-desktop kernel: [ 8978.743206] sd 18:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:48 zion-desktop kernel: [ 8978.743957] sd 18:0:0:0: [sde] Write Protect is off
Nov 12 19:11:48 zion-desktop kernel: [ 8978.743965]  sde: sde1
Nov 12 19:11:48 zion-desktop kernel: [ 8978.771757] sd 18:0:0:0: [sde] Attached SCSI disk
Nov 12 19:11:48 zion-desktop kernel: [ 8978.771792] sd 18:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:11:53 zion-desktop kernel: [ 8984.039615] usb 3-8: USB disconnect, address 20
Nov 12 19:11:53 zion-desktop kernel: [ 8984.310237] usb 3-8: new high speed USB device using ehci_hcd and address 21
Nov 12 19:11:54 zion-desktop kernel: [ 8984.699531] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:11:54 zion-desktop kernel: [ 8984.699773] scsi19 : SCSI emulation for USB Mass Storage devices
Nov 12 19:11:59 zion-desktop kernel: [ 8989.697788] scsi 19:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:11:59 zion-desktop kernel: [ 8989.699270] sd 19:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:59 zion-desktop kernel: [ 8989.700144] sd 19:0:0:0: [sde] Write Protect is off
Nov 12 19:11:59 zion-desktop kernel: [ 8989.700894] sd 19:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:11:59 zion-desktop kernel: [ 8989.701768] sd 19:0:0:0: [sde] Write Protect is off
Nov 12 19:11:59 zion-desktop kernel: [ 8989.701776]  sde: sde1
Nov 12 19:11:59 zion-desktop kernel: [ 8989.729703] sd 19:0:0:0: [sde] Attached SCSI disk
Nov 12 19:11:59 zion-desktop kernel: [ 8989.729739] sd 19:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:12:00 zion-desktop kernel: [ 8990.545626] usb 3-8: USB disconnect, address 21
Nov 12 19:12:00 zion-desktop kernel: [ 8990.656908] printk: 386 messages suppressed.
Nov 12 19:12:00 zion-desktop kernel: [ 8990.816973] usb 3-8: new high speed USB device using ehci_hcd and address 22
Nov 12 19:12:00 zion-desktop kernel: [ 8991.214285] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:12:00 zion-desktop kernel: [ 8991.214527] scsi20 : SCSI emulation for USB Mass Storage devices
Nov 12 19:12:05 zion-desktop kernel: [ 8996.212536] scsi 20:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:12:05 zion-desktop kernel: [ 8996.214018] sd 20:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:05 zion-desktop kernel: [ 8996.214892] sd 20:0:0:0: [sde] Write Protect is off
Nov 12 19:12:05 zion-desktop kernel: [ 8996.215642] sd 20:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:05 zion-desktop kernel: [ 8996.216516] sd 20:0:0:0: [sde] Write Protect is off
Nov 12 19:12:05 zion-desktop kernel: [ 8996.216524]  sde: sde1
Nov 12 19:12:05 zion-desktop kernel: [ 8996.241190] sd 20:0:0:0: [sde] Attached SCSI disk
Nov 12 19:12:05 zion-desktop kernel: [ 8996.241224] sd 20:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:12:17 zion-desktop kernel: [ 9007.548267] usb 3-8: USB disconnect, address 22
Nov 12 19:12:17 zion-desktop kernel: [ 9007.889668] usb 3-8: new high speed USB device using ehci_hcd and address 23
Nov 12 19:12:17 zion-desktop kernel: [ 9008.275047] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:12:17 zion-desktop kernel: [ 9008.275289] scsi21 : SCSI emulation for USB Mass Storage devices
Nov 12 19:12:22 zion-desktop kernel: [ 9013.273302] scsi 21:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:12:22 zion-desktop kernel: [ 9013.274784] sd 21:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:22 zion-desktop kernel: [ 9013.275658] sd 21:0:0:0: [sde] Write Protect is off
Nov 12 19:12:22 zion-desktop kernel: [ 9013.276641] sd 21:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:22 zion-desktop kernel: [ 9013.277407] sd 21:0:0:0: [sde] Write Protect is off
Nov 12 19:12:22 zion-desktop kernel: [ 9013.277416]  sde: sde1
Nov 12 19:12:22 zion-desktop kernel: [ 9013.302735] sd 21:0:0:0: [sde] Attached SCSI disk
Nov 12 19:12:22 zion-desktop kernel: [ 9013.302772] sd 21:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:12:46 zion-desktop kernel: [ 9037.361825] usb 3-8: USB disconnect, address 23
Nov 12 19:12:46 zion-desktop kernel: [ 9037.362060] printk: 3 messages suppressed.
Nov 12 19:12:46 zion-desktop kernel: [ 9037.362066] lost page write due to I/O error on sde1
Nov 12 19:12:46 zion-desktop kernel: [ 9037.362073] lost page write due to I/O error on sde1
Nov 12 19:12:46 zion-desktop kernel: [ 9037.362078] lost page write due to I/O error on sde1
Nov 12 19:12:46 zion-desktop kernel: [ 9037.362083] lost page write due to I/O error on sde1
Nov 12 19:12:47 zion-desktop kernel: [ 9037.631931] usb 3-8: new high speed USB device using ehci_hcd and address 24
Nov 12 19:12:48 zion-desktop kernel: [ 9038.511757] usb 3-8: new high speed USB device using ehci_hcd and address 25
Nov 12 19:12:48 zion-desktop kernel: [ 9038.901183] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:12:48 zion-desktop kernel: [ 9038.901424] scsi22 : SCSI emulation for USB Mass Storage devices
Nov 12 19:12:53 zion-desktop kernel: [ 9043.899312] scsi 22:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:12:53 zion-desktop kernel: [ 9043.901047] sd 22:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:53 zion-desktop kernel: [ 9043.901921] sd 22:0:0:0: [sde] Write Protect is off
Nov 12 19:12:53 zion-desktop kernel: [ 9043.902670] sd 22:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:12:53 zion-desktop kernel: [ 9043.903419] sd 22:0:0:0: [sde] Write Protect is off
Nov 12 19:12:53 zion-desktop kernel: [ 9043.903427]  sde: sde1
Nov 12 19:12:53 zion-desktop kernel: [ 9043.928479] sd 22:0:0:0: [sde] Attached SCSI disk
Nov 12 19:12:53 zion-desktop kernel: [ 9043.928514] sd 22:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:13:03 zion-desktop kernel: [ 9054.038112] usb 3-8: USB disconnect, address 25
Nov 12 19:13:03 zion-desktop kernel: [ 9054.308716] usb 3-8: new high speed USB device using ehci_hcd and address 26
Nov 12 19:13:04 zion-desktop kernel: [ 9054.694215] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:13:04 zion-desktop kernel: [ 9054.694459] scsi23 : SCSI emulation for USB Mass Storage devices
Nov 12 19:13:05 zion-desktop kernel: [ 9055.769312] usb 3-8: USB disconnect, address 26
Nov 12 19:13:16 zion-desktop kernel: [ 9067.142223] usb 3-8: new high speed USB device using ehci_hcd and address 27
Nov 12 19:13:17 zion-desktop kernel: [ 9067.535733] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:13:17 zion-desktop kernel: [ 9067.535975] scsi24 : SCSI emulation for USB Mass Storage devices
Nov 12 19:13:22 zion-desktop kernel: [ 9072.533885] scsi 24:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:13:22 zion-desktop kernel: [ 9072.535347] sd 24:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:13:22 zion-desktop kernel: [ 9072.536220] sd 24:0:0:0: [sde] Write Protect is off
Nov 12 19:13:22 zion-desktop kernel: [ 9072.536970] sd 24:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:13:22 zion-desktop kernel: [ 9072.537719] sd 24:0:0:0: [sde] Write Protect is off
Nov 12 19:13:22 zion-desktop kernel: [ 9072.537727]  sde: sde1
Nov 12 19:13:22 zion-desktop kernel: [ 9072.564173] sd 24:0:0:0: [sde] Attached SCSI disk
Nov 12 19:13:22 zion-desktop kernel: [ 9072.564210] sd 24:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:13:22 zion-desktop kernel: [ 9073.325340] usb 3-8: USB disconnect, address 27
Nov 12 19:13:23 zion-desktop kernel: [ 9073.597545] usb 3-8: new high speed USB device using ehci_hcd and address 28
Nov 12 19:13:24 zion-desktop kernel: [ 9074.696764] usb 3-8: new high speed USB device using ehci_hcd and address 29
Nov 12 19:13:24 zion-desktop kernel: [ 9075.086272] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:13:24 zion-desktop kernel: [ 9075.086514] scsi25 : SCSI emulation for USB Mass Storage devices
Nov 12 19:13:29 zion-desktop kernel: [ 9080.084402] scsi 25:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:13:29 zion-desktop kernel: [ 9080.085884] sd 25:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:13:29 zion-desktop kernel: [ 9080.086758] sd 25:0:0:0: [sde] Write Protect is off
Nov 12 19:13:29 zion-desktop kernel: [ 9080.087506] sd 25:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:13:29 zion-desktop kernel: [ 9080.088256] sd 25:0:0:0: [sde] Write Protect is off
Nov 12 19:13:29 zion-desktop kernel: [ 9080.088263]  sde: sde1
Nov 12 19:13:29 zion-desktop kernel: [ 9080.108205] sd 25:0:0:0: [sde] Attached SCSI disk
Nov 12 19:13:29 zion-desktop kernel: [ 9080.108241] sd 25:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:14:06 zion-desktop kernel: [ 9117.126965] usb 3-8: USB disconnect, address 29
Nov 12 19:14:07 zion-desktop kernel: [ 9117.648469] usb 3-8: new high speed USB device using ehci_hcd and address 30
Nov 12 19:14:07 zion-desktop kernel: [ 9118.037783] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:14:07 zion-desktop kernel: [ 9118.054865] scsi26 : SCSI emulation for USB Mass Storage devices
Nov 12 19:14:12 zion-desktop kernel: [ 9122.664126] usb 3-8: USB disconnect, address 30
Nov 12 19:14:23 zion-desktop kernel: [ 9134.341239] usb 3-8: new high speed USB device using ehci_hcd and address 31
Nov 12 19:14:28 zion-desktop kernel: [ 9138.577809] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:14:28 zion-desktop kernel: [ 9138.578051] scsi27 : SCSI emulation for USB Mass Storage devices
Nov 12 19:14:38 zion-desktop kernel: [ 9149.186372] usb 3-8: reset high speed USB device using ehci_hcd and address 31
Nov 12 19:14:39 zion-desktop kernel: [ 9149.576886] scsi 27:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:14:39 zion-desktop kernel: [ 9149.582987] sd 27:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:14:39 zion-desktop kernel: [ 9149.583860] sd 27:0:0:0: [sde] Write Protect is off
Nov 12 19:14:39 zion-desktop kernel: [ 9149.584733] sd 27:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:14:39 zion-desktop kernel: [ 9149.585358] sd 27:0:0:0: [sde] Write Protect is off
Nov 12 19:14:39 zion-desktop kernel: [ 9149.585366]  sde: sde1
Nov 12 19:14:39 zion-desktop kernel: [ 9149.608912] sd 27:0:0:0: [sde] Attached SCSI disk
Nov 12 19:14:39 zion-desktop kernel: [ 9149.608947] sd 27:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:14:47 zion-desktop kernel: [ 9158.137449] usb 3-8: USB disconnect, address 31
Nov 12 19:14:48 zion-desktop kernel: [ 9158.408623] usb 3-8: new high speed USB device using ehci_hcd and address 32
Nov 12 19:14:48 zion-desktop kernel: [ 9158.793991] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:14:48 zion-desktop kernel: [ 9158.794231] scsi28 : SCSI emulation for USB Mass Storage devices
Nov 12 19:14:53 zion-desktop kernel: [ 9163.792120] scsi 28:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:14:53 zion-desktop kernel: [ 9163.793602] sd 28:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:14:53 zion-desktop kernel: [ 9163.794476] sd 28:0:0:0: [sde] Write Protect is off
Nov 12 19:14:53 zion-desktop kernel: [ 9163.795226] sd 28:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:14:53 zion-desktop kernel: [ 9163.796100] sd 28:0:0:0: [sde] Write Protect is off
Nov 12 19:14:53 zion-desktop kernel: [ 9163.796108]  sde: sde1
Nov 12 19:14:53 zion-desktop kernel: [ 9163.822650] sd 28:0:0:0: [sde] Attached SCSI disk
Nov 12 19:14:53 zion-desktop kernel: [ 9163.822684] sd 28:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:14:56 zion-desktop kernel: [ 9167.098810] usb 3-8: USB disconnect, address 32
Nov 12 19:14:56 zion-desktop kernel: [ 9167.370876] usb 3-8: new high speed USB device using ehci_hcd and address 33
Nov 12 19:14:57 zion-desktop kernel: [ 9167.752224] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:14:57 zion-desktop kernel: [ 9167.752527] scsi29 : SCSI emulation for USB Mass Storage devices
Nov 12 19:15:02 zion-desktop kernel: [ 9172.750481] scsi 29:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:15:02 zion-desktop kernel: [ 9172.751963] sd 29:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:15:02 zion-desktop kernel: [ 9172.752837] sd 29:0:0:0: [sde] Write Protect is off
Nov 12 19:15:02 zion-desktop kernel: [ 9172.753587] sd 29:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:15:02 zion-desktop kernel: [ 9172.754461] sd 29:0:0:0: [sde] Write Protect is off
Nov 12 19:15:02 zion-desktop kernel: [ 9172.754469]  sde: sde1
Nov 12 19:15:02 zion-desktop kernel: [ 9172.782259] sd 29:0:0:0: [sde] Attached SCSI disk
Nov 12 19:15:02 zion-desktop kernel: [ 9172.782294] sd 29:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:15:03 zion-desktop kernel: [ 9173.933996] usb 3-8: USB disconnect, address 33
Nov 12 19:15:03 zion-desktop kernel: [ 9174.205556] usb 3-8: new high speed USB device using ehci_hcd and address 34
Nov 12 19:15:04 zion-desktop kernel: [ 9174.598907] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:15:04 zion-desktop kernel: [ 9174.599147] scsi30 : SCSI emulation for USB Mass Storage devices
Nov 12 19:15:09 zion-desktop kernel: [ 9179.597162] scsi 30:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:15:09 zion-desktop kernel: [ 9179.598643] sd 30:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:15:09 zion-desktop kernel: [ 9179.599517] sd 30:0:0:0: [sde] Write Protect is off
Nov 12 19:15:09 zion-desktop kernel: [ 9179.600266] sd 30:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:15:09 zion-desktop kernel: [ 9179.601140] sd 30:0:0:0: [sde] Write Protect is off
Nov 12 19:15:09 zion-desktop kernel: [ 9179.601148]  sde: sde1
Nov 12 19:15:09 zion-desktop kernel: [ 9179.626819] sd 30:0:0:0: [sde] Attached SCSI disk
Nov 12 19:15:09 zion-desktop kernel: [ 9179.626854] sd 30:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:15:12 zion-desktop kernel: [ 9182.657777] usb 3-8: USB disconnect, address 34
Nov 12 19:16:24 zion-desktop kernel: [ 9254.789965] usb 3-8: new high speed USB device using ehci_hcd and address 35
Nov 12 19:16:24 zion-desktop kernel: [ 9255.183478] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:16:24 zion-desktop kernel: [ 9255.183718] scsi31 : SCSI emulation for USB Mass Storage devices
Nov 12 19:16:29 zion-desktop kernel: [ 9260.181606] scsi 31:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:16:29 zion-desktop kernel: [ 9260.183088] sd 31:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:29 zion-desktop kernel: [ 9260.183962] sd 31:0:0:0: [sde] Write Protect is off
Nov 12 19:16:29 zion-desktop kernel: [ 9260.184712] sd 31:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:29 zion-desktop kernel: [ 9260.185461] sd 31:0:0:0: [sde] Write Protect is off
Nov 12 19:16:29 zion-desktop kernel: [ 9260.185469]  sde: sde1
Nov 12 19:16:29 zion-desktop kernel: [ 9260.215729] sd 31:0:0:0: [sde] Attached SCSI disk
Nov 12 19:16:29 zion-desktop kernel: [ 9260.215766] sd 31:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:16:29 zion-desktop kernel: [ 9260.262598] usb 3-8: USB disconnect, address 35
Nov 12 19:16:30 zion-desktop kernel: [ 9260.532865] usb 3-8: new high speed USB device using ehci_hcd and address 36
Nov 12 19:16:30 zion-desktop kernel: [ 9260.930263] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:16:30 zion-desktop kernel: [ 9260.930506] scsi32 : SCSI emulation for USB Mass Storage devices
Nov 12 19:16:31 zion-desktop kernel: [ 9261.964743] usb 3-8: USB disconnect, address 36
Nov 12 19:16:31 zion-desktop kernel: [ 9262.236530] usb 3-8: new high speed USB device using ehci_hcd and address 37
Nov 12 19:16:32 zion-desktop kernel: [ 9262.629912] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:16:32 zion-desktop kernel: [ 9262.630150] scsi33 : SCSI emulation for USB Mass Storage devices
Nov 12 19:16:37 zion-desktop kernel: [ 9267.628187] scsi 33:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:16:37 zion-desktop kernel: [ 9267.630037] sd 33:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:37 zion-desktop kernel: [ 9267.630896] sd 33:0:0:0: [sde] Write Protect is off
Nov 12 19:16:37 zion-desktop kernel: [ 9267.631521] sd 33:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:37 zion-desktop kernel: [ 9267.632396] sd 33:0:0:0: [sde] Write Protect is off
Nov 12 19:16:37 zion-desktop kernel: [ 9267.632404]  sde: sde1
Nov 12 19:16:37 zion-desktop kernel: [ 9267.657479] sd 33:0:0:0: [sde] Attached SCSI disk
Nov 12 19:16:37 zion-desktop kernel: [ 9267.657516] sd 33:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:16:50 zion-desktop kernel: [ 9280.528315] usb 3-8: USB disconnect, address 37
Nov 12 19:16:50 zion-desktop kernel: [ 9280.796964] usb 3-8: new high speed USB device using ehci_hcd and address 38
Nov 12 19:16:50 zion-desktop kernel: [ 9281.182355] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:16:50 zion-desktop kernel: [ 9281.182597] scsi34 : SCSI emulation for USB Mass Storage devices
Nov 12 19:16:55 zion-desktop kernel: [ 9286.180481] scsi 34:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:16:55 zion-desktop kernel: [ 9286.181972] sd 34:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:55 zion-desktop kernel: [ 9286.182842] sd 34:0:0:0: [sde] Write Protect is off
Nov 12 19:16:55 zion-desktop kernel: [ 9286.183591] sd 34:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:16:55 zion-desktop kernel: [ 9286.184465] sd 34:0:0:0: [sde] Write Protect is off
Nov 12 19:16:55 zion-desktop kernel: [ 9286.184473]  sde: sde1
Nov 12 19:16:55 zion-desktop kernel: [ 9286.209391] sd 34:0:0:0: [sde] Attached SCSI disk
Nov 12 19:16:55 zion-desktop kernel: [ 9286.209424] sd 34:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:16:59 zion-desktop kernel: [ 9290.362112] usb 3-8: USB disconnect, address 38
Nov 12 19:17:00 zion-desktop kernel: [ 9290.631060] usb 3-8: new high speed USB device using ehci_hcd and address 39
Nov 12 19:17:00 zion-desktop kernel: [ 9291.024402] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:00 zion-desktop kernel: [ 9291.024645] scsi35 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:05 zion-desktop kernel: [ 9295.748474] usb 3-8: USB disconnect, address 39
Nov 12 19:17:05 zion-desktop kernel: [ 9296.018004] usb 3-8: new high speed USB device using ehci_hcd and address 40
Nov 12 19:17:06 zion-desktop kernel: [ 9296.411393] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:06 zion-desktop kernel: [ 9296.411634] scsi36 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:08 zion-desktop kernel: [ 9299.192127] usb 3-8: USB disconnect, address 40
Nov 12 19:17:22 zion-desktop kernel: [ 9312.574800] usb 3-8: new high speed USB device using ehci_hcd and address 41
Nov 12 19:17:26 zion-desktop kernel: [ 9316.811483] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:26 zion-desktop kernel: [ 9316.811721] scsi37 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:29 zion-desktop kernel: [ 9320.060109] usb 3-8: USB disconnect, address 41
Nov 12 19:17:29 zion-desktop kernel: [ 9320.329305] usb 3-8: new high speed USB device using ehci_hcd and address 42
Nov 12 19:17:30 zion-desktop kernel: [ 9320.702781] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:30 zion-desktop kernel: [ 9320.703602] scsi38 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:35 zion-desktop kernel: [ 9325.700911] scsi 38:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:17:35 zion-desktop kernel: [ 9325.702268] sd 38:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:35 zion-desktop kernel: [ 9325.703142] sd 38:0:0:0: [sde] Write Protect is off
Nov 12 19:17:35 zion-desktop kernel: [ 9325.703892] sd 38:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:35 zion-desktop kernel: [ 9325.704766] sd 38:0:0:0: [sde] Write Protect is off
Nov 12 19:17:35 zion-desktop kernel: [ 9325.704773]  sde: sde1
Nov 12 19:17:35 zion-desktop kernel: [ 9325.715719] sd 38:0:0:0: [sde] Attached SCSI disk
Nov 12 19:17:35 zion-desktop kernel: [ 9325.715755] sd 38:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:17:36 zion-desktop kernel: [ 9326.884724] usb 3-8: USB disconnect, address 42
Nov 12 19:17:36 zion-desktop kernel: [ 9327.156002] usb 3-8: new high speed USB device using ehci_hcd and address 43
Nov 12 19:17:37 zion-desktop kernel: [ 9327.541464] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:37 zion-desktop kernel: [ 9327.541705] scsi39 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:42 zion-desktop kernel: [ 9332.539593] scsi 39:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:17:42 zion-desktop kernel: [ 9332.541075] sd 39:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:42 zion-desktop kernel: [ 9332.541948] sd 39:0:0:0: [sde] Write Protect is off
Nov 12 19:17:42 zion-desktop kernel: [ 9332.542698] sd 39:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:42 zion-desktop kernel: [ 9332.543572] sd 39:0:0:0: [sde] Write Protect is off
Nov 12 19:17:42 zion-desktop kernel: [ 9332.543580]  sde: sde1
Nov 12 19:17:42 zion-desktop kernel: [ 9332.568498] sd 39:0:0:0: [sde] Attached SCSI disk
Nov 12 19:17:42 zion-desktop kernel: [ 9332.568532] sd 39:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:17:45 zion-desktop kernel: [ 9335.797682] usb 3-8: USB disconnect, address 43
Nov 12 19:17:45 zion-desktop kernel: [ 9336.070274] usb 3-8: new high speed USB device using ehci_hcd and address 44
Nov 12 19:17:46 zion-desktop kernel: [ 9336.459582] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:17:46 zion-desktop kernel: [ 9336.466847] scsi40 : SCSI emulation for USB Mass Storage devices
Nov 12 19:17:51 zion-desktop kernel: [ 9341.465842] scsi 40:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:17:51 zion-desktop kernel: [ 9341.467562] sd 40:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:51 zion-desktop kernel: [ 9341.468435] sd 40:0:0:0: [sde] Write Protect is off
Nov 12 19:17:51 zion-desktop kernel: [ 9341.469185] sd 40:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:17:51 zion-desktop kernel: [ 9341.469934] sd 40:0:0:0: [sde] Write Protect is off
Nov 12 19:17:51 zion-desktop kernel: [ 9341.469942]  sde: sde1
Nov 12 19:17:51 zion-desktop kernel: [ 9341.494858] sd 40:0:0:0: [sde] Attached SCSI disk
Nov 12 19:17:51 zion-desktop kernel: [ 9341.494893] sd 40:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:18:09 zion-desktop kernel: [ 9359.947042] usb 3-8: USB disconnect, address 44
Nov 12 19:18:09 zion-desktop kernel: [ 9360.217615] usb 3-8: new high speed USB device using ehci_hcd and address 45
Nov 12 19:18:10 zion-desktop kernel: [ 9360.606959] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:18:10 zion-desktop kernel: [ 9360.607200] scsi41 : SCSI emulation for USB Mass Storage devices
Nov 12 19:18:11 zion-desktop kernel: [ 9362.088349] usb 3-8: USB disconnect, address 45
Nov 12 19:18:11 zion-desktop kernel: [ 9362.357198] usb 3-8: new high speed USB device using ehci_hcd and address 46
Nov 12 19:18:12 zion-desktop kernel: [ 9362.754506] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:18:12 zion-desktop kernel: [ 9362.754753] scsi42 : SCSI emulation for USB Mass Storage devices
Nov 12 19:18:14 zion-desktop kernel: [ 9365.152952] usb 3-8: USB disconnect, address 46
Nov 12 19:18:39 zion-desktop kernel: [ 9389.852001] device eth0 left promiscuous mode
Nov 12 19:18:39 zion-desktop kernel: [ 9389.852014] audit(1194866319.035:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov 12 19:18:45 zion-desktop kernel: [ 9396.281352] nfsd: last server has exited
Nov 12 19:18:45 zion-desktop kernel: [ 9396.281355] nfsd: unexporting all filesystems
Nov 12 19:18:46 zion-desktop exiting on signal 15
Nov 12 19:22:04 zion-desktop syslogd 1.4.1#21ubuntu3: restart.
Nov 12 19:22:04 zion-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 12 19:22:04 zion-desktop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 12 19:22:04 zion-desktop kernel: Symbols match kernel version 2.6.22.
Nov 12 19:22:04 zion-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 00000000fefffc00 - 00000000ff000000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] 1151MB HIGHMEM available.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] 896MB LOWMEM available.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] found SMP MP-table at 000f5750
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]   DMA             0 ->     4096
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]   HighMem    229376 ->   524272
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 12 19:22:04 zion-desktop kernel: [    0.000000]     0:        0 ->   524272
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] DMI 2.2 present.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F71A0 checksum 0
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: RSDP 000F71A0, 0014 (r0 Nvidia)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: DSDT 7FFF30C0, 494D (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: FACS 7FFF0000, 0040
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: APIC 7FFF7A40, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Processor #0 15:15 APIC version 16
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Built 1 zonelists.  Total pages: 520177
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Kernel command line: root=UUID=5876fa45-39d0-459f-a4fc-157afeeb1bd7 ro quiet splash
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Initializing CPU#0
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 12 19:22:04 zion-desktop kernel: [    0.000000] Detected 1808.796 MHz processor.
Nov 12 19:22:04 zion-desktop kernel: [   23.703734] Console: colour VGA+ 80x25
Nov 12 19:22:04 zion-desktop kernel: [   23.704074] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   23.704446] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   23.772728] Memory: 2067456k/2097088k available (2015k kernel code, 28424k reserved, 916k data, 364k init, 1179584k highmem)
Nov 12 19:22:04 zion-desktop kernel: [   23.772739] virtual kernel memory layout:
Nov 12 19:22:04 zion-desktop kernel: [   23.772740]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772741]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772742]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772744]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772745]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772746]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772748]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov 12 19:22:04 zion-desktop kernel: [   23.772751] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 12 19:22:04 zion-desktop kernel: [   23.772787] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Nov 12 19:22:04 zion-desktop kernel: [   23.852791] Calibrating delay using timer specific routine.. 3619.97 BogoMIPS (lpj=7239950)
Nov 12 19:22:04 zion-desktop kernel: [   23.852817] Security Framework v1.0.0 initialized
Nov 12 19:22:04 zion-desktop kernel: [   23.852822] SELinux:  Disabled at boot.
Nov 12 19:22:04 zion-desktop kernel: [   23.852835] Mount-cache hash table entries: 512
Nov 12 19:22:04 zion-desktop kernel: [   23.852954] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 12 19:22:04 zion-desktop kernel: [   23.852957] CPU: L2 Cache: 512K (64 bytes/line)
Nov 12 19:22:04 zion-desktop kernel: [   23.852970] Compat vDSO mapped to ffffe000.
Nov 12 19:22:04 zion-desktop kernel: [   23.852980] Checking 'hlt' instruction... OK.
Nov 12 19:22:04 zion-desktop kernel: [   23.868914] SMP alternatives: switching to UP code
Nov 12 19:22:04 zion-desktop kernel: [   23.869095] Freeing SMP alternatives: 11k freed
Nov 12 19:22:04 zion-desktop kernel: [   23.869347] Early unpacking initramfs... done
Nov 12 19:22:04 zion-desktop kernel: [   24.198723] ACPI: Core revision 20070126
Nov 12 19:22:04 zion-desktop kernel: [   24.198786] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 12 19:22:04 zion-desktop kernel: [   24.201504] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
Nov 12 19:22:04 zion-desktop kernel: [   24.201519] Total of 1 processors activated (3619.97 BogoMIPS).
Nov 12 19:22:04 zion-desktop kernel: [   24.201630] ENABLING IO-APIC IRQs
Nov 12 19:22:04 zion-desktop kernel: [   24.201787] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov 12 19:22:04 zion-desktop kernel: [   24.348760] Brought up 1 CPUs
Nov 12 19:22:04 zion-desktop kernel: [   24.348848] Booting paravirtualized kernel on bare hardware
Nov 12 19:22:04 zion-desktop kernel: [   24.348888] Time: 11:21:43  Date: 10/12/107
Nov 12 19:22:04 zion-desktop kernel: [   24.348905] NET: Registered protocol family 16
Nov 12 19:22:04 zion-desktop kernel: [   24.348970] EISA bus registered
Nov 12 19:22:04 zion-desktop kernel: [   24.348978] ACPI: bus type pci registered
Nov 12 19:22:04 zion-desktop kernel: [   24.377914] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
Nov 12 19:22:04 zion-desktop kernel: [   24.377916] PCI: Using configuration type 1
Nov 12 19:22:04 zion-desktop kernel: [   24.377918] Setting up standard PCI resources
Nov 12 19:22:04 zion-desktop kernel: [   24.387911] ACPI: Interpreter enabled
Nov 12 19:22:04 zion-desktop kernel: [   24.387914] ACPI: (supports S0 S1 S4 S5)
Nov 12 19:22:04 zion-desktop kernel: [   24.387927] ACPI: Using IOAPIC for interrupt routing
Nov 12 19:22:04 zion-desktop kernel: [   24.396566] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 12 19:22:04 zion-desktop kernel: [   24.448565] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.448744] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.448917] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.449092] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.449271] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.449445] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.449619] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.449791] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.449965] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.450139] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.450312] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.450487] ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.450664] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.450840] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.451014] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.451188] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.451370] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.451553] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 12 19:22:04 zion-desktop kernel: [   24.451753] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.451937] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.452120] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.452304] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.452434] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
Nov 12 19:22:04 zion-desktop kernel: [   24.452624] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.452815] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.453004] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.453197] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.453386] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.453575] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.453764] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.453952] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.454141] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.454330] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.454519] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.454715] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.454910] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Nov 12 19:22:04 zion-desktop kernel: [   24.455038] ACPI: Power Resource [ISAV] (on)
Nov 12 19:22:04 zion-desktop kernel: [   24.455055] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 12 19:22:04 zion-desktop kernel: [   24.455064] pnp: PnP ACPI init
Nov 12 19:22:04 zion-desktop kernel: [   24.455073] ACPI: bus type pnp registered
Nov 12 19:22:04 zion-desktop kernel: [   24.459209] pnp: PnP ACPI: found 12 devices
Nov 12 19:22:04 zion-desktop kernel: [   24.459211] ACPI: ACPI bus type pnp unregistered
Nov 12 19:22:04 zion-desktop kernel: [   24.459214] PnPBIOS: Disabled by ACPI PNP
Nov 12 19:22:04 zion-desktop kernel: [   24.459253] PCI: Using ACPI for IRQ routing
Nov 12 19:22:04 zion-desktop kernel: [   24.459257] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 12 19:22:04 zion-desktop kernel: [   24.488701] NET: Registered protocol family 8
Nov 12 19:22:04 zion-desktop kernel: [   24.488703] NET: Registered protocol family 20
Nov 12 19:22:04 zion-desktop kernel: [   24.488754] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488757] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488760] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488763] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488766] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488769] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488774] pnp: 00:01: iomem range 0xd5000-0xd7fff has been reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488777] pnp: 00:01: iomem range 0xf0000-0xf7fff could not be reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488780] pnp: 00:01: iomem range 0xf8000-0xfbfff could not be reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.488783] pnp: 00:01: iomem range 0xfc000-0xfffff could not be reserved
Nov 12 19:22:04 zion-desktop kernel: [   24.492710] Time: tsc clocksource has been installed.
Nov 12 19:22:04 zion-desktop kernel: [   24.519011] PCI: Bridge: 0000:00:0b.0
Nov 12 19:22:04 zion-desktop kernel: [   24.519013]   IO window: disabled.
Nov 12 19:22:04 zion-desktop kernel: [   24.519017]   MEM window: f8000000-f9ffffff
Nov 12 19:22:04 zion-desktop kernel: [   24.519021]   PREFETCH window: e0000000-efffffff
Nov 12 19:22:04 zion-desktop kernel: [   24.519025] PCI: Bridge: 0000:00:0e.0
Nov 12 19:22:04 zion-desktop kernel: [   24.519027]   IO window: 9000-9fff
Nov 12 19:22:04 zion-desktop kernel: [   24.519030]   MEM window: fa000000-fbffffff
Nov 12 19:22:04 zion-desktop kernel: [   24.519033]   PREFETCH window: 88000000-880fffff
Nov 12 19:22:04 zion-desktop kernel: [   24.519055] NET: Registered protocol family 2
Nov 12 19:22:04 zion-desktop kernel: [   24.556734] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   24.556839] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   24.557947] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   24.558343] TCP: Hash tables configured (established 131072 bind 65536)
Nov 12 19:22:04 zion-desktop kernel: [   24.558346] TCP reno registered
Nov 12 19:22:04 zion-desktop kernel: [   24.568818] checking if image is initramfs... it is
Nov 12 19:22:04 zion-desktop kernel: [   25.020643] Switched to high resolution mode on CPU 0
Nov 12 19:22:04 zion-desktop kernel: [   25.213912] Freeing initrd memory: 7342k freed
Nov 12 19:22:04 zion-desktop kernel: [   25.214231] audit: initializing netlink socket (disabled)
Nov 12 19:22:04 zion-desktop kernel: [   25.214243] audit(1194866503.120:1): initialized
Nov 12 19:22:04 zion-desktop kernel: [   25.214296] highmem bounce pool size: 64 pages
Nov 12 19:22:04 zion-desktop kernel: [   25.215753] VFS: Disk quotas dquot_6.5.1
Nov 12 19:22:04 zion-desktop kernel: [   25.215793] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 12 19:22:04 zion-desktop kernel: [   25.215869] io scheduler noop registered
Nov 12 19:22:04 zion-desktop kernel: [   25.215871] io scheduler anticipatory registered
Nov 12 19:22:04 zion-desktop kernel: [   25.215873] io scheduler deadline registered
Nov 12 19:22:04 zion-desktop kernel: [   25.215886] io scheduler cfq registered (default)
Nov 12 19:22:04 zion-desktop kernel: [   25.244645] isapnp: Scanning for PnP cards...
Nov 12 19:22:04 zion-desktop kernel: [   25.598316] isapnp: No Plug & Play device found
Nov 12 19:22:04 zion-desktop kernel: [   25.618690] Real Time Clock Driver v1.12ac
Nov 12 19:22:04 zion-desktop kernel: [   25.618767] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 12 19:22:04 zion-desktop kernel: [   25.618844] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 12 19:22:04 zion-desktop kernel: [   25.619376] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 12 19:22:04 zion-desktop kernel: [   25.619918] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 12 19:22:04 zion-desktop kernel: [   25.620082] input: Macintosh mouse button emulation as /class/input/input0
Nov 12 19:22:04 zion-desktop kernel: [   25.620137] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov 12 19:22:04 zion-desktop kernel: [   25.620140] PNP: PS/2 controller doesn't have AUX irq; using default 12
Nov 12 19:22:04 zion-desktop kernel: [   25.622540] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 12 19:22:04 zion-desktop kernel: [   25.622545] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 12 19:22:04 zion-desktop kernel: [   25.622680] mice: PS/2 mouse device common for all mice
Nov 12 19:22:04 zion-desktop kernel: [   25.622767] EISA: Probing bus 0 at eisa.0
Nov 12 19:22:04 zion-desktop kernel: [   25.622781] Cannot allocate resource for EISA slot 4
Nov 12 19:22:04 zion-desktop kernel: [   25.622792] EISA: Detected 0 cards.
Nov 12 19:22:04 zion-desktop kernel: [   25.622873] TCP cubic registered
Nov 12 19:22:04 zion-desktop kernel: [   25.622884] NET: Registered protocol family 1
Nov 12 19:22:04 zion-desktop kernel: [   25.622903] Using IPI No-Shortcut mode
Nov 12 19:22:04 zion-desktop kernel: [   25.623041]   Magic number: 15:918:377
Nov 12 19:22:04 zion-desktop kernel: [   25.623156]   hash matches device PNP0700:00
Nov 12 19:22:04 zion-desktop kernel: [   25.623380] Freeing unused kernel memory: 364k freed
Nov 12 19:22:04 zion-desktop kernel: [   25.664432] input: AT Translated Set 2 keyboard as /class/input/input1
Nov 12 19:22:04 zion-desktop kernel: [   26.876102] AppArmor: AppArmor initialized<5>audit(1194866504.620:2):  type=1505 info="AppArmor initialized" pid=1345
Nov 12 19:22:04 zion-desktop kernel: [   26.884449] fuse init (API version 7.8)
Nov 12 19:22:04 zion-desktop kernel: [   26.890139] Failure registering capabilities with primary security module.
Nov 12 19:22:04 zion-desktop kernel: [   27.482911] usbcore: registered new interface driver usbfs
Nov 12 19:22:04 zion-desktop kernel: [   27.482935] usbcore: registered new interface driver hub
Nov 12 19:22:04 zion-desktop kernel: [   27.482953] usbcore: registered new device driver usb
Nov 12 19:22:04 zion-desktop kernel: [   27.483899] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Nov 12 19:22:04 zion-desktop kernel: [   27.483905] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, high) -> IRQ 16
Nov 12 19:22:04 zion-desktop kernel: [   27.483919] ohci_hcd 0000:00:02.0: OHCI Host Controller
Nov 12 19:22:04 zion-desktop kernel: [   27.499798] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Nov 12 19:22:04 zion-desktop kernel: [   27.499815] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfc002000
Nov 12 19:22:04 zion-desktop kernel: [   27.533166] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 12 19:22:04 zion-desktop kernel: [   27.533171] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 12 19:22:04 zion-desktop kernel: [   27.542641] SCSI subsystem initialized
Nov 12 19:22:04 zion-desktop kernel: [   27.558221] usb usb1: configuration #1 chosen from 1 choice
Nov 12 19:22:04 zion-desktop kernel: [   27.558247] hub 1-0:1.0: USB hub found
Nov 12 19:22:04 zion-desktop kernel: [   27.558255] hub 1-0:1.0: 4 ports detected
Nov 12 19:22:04 zion-desktop kernel: [   27.660279] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 22
Nov 12 19:22:04 zion-desktop kernel: [   27.660287] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 22 (level, high) -> IRQ 17
Nov 12 19:22:04 zion-desktop kernel: [   27.660301] ohci_hcd 0000:00:02.1: OHCI Host Controller
Nov 12 19:22:04 zion-desktop kernel: [   27.660323] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Nov 12 19:22:04 zion-desktop kernel: [   27.660336] ohci_hcd 0000:00:02.1: irq 17, io mem 0xfc003000
Nov 12 19:22:04 zion-desktop kernel: [   27.717911] usb usb2: configuration #1 chosen from 1 choice
Nov 12 19:22:04 zion-desktop kernel: [   27.717936] hub 2-0:1.0: USB hub found
Nov 12 19:22:04 zion-desktop kernel: [   27.717944] hub 2-0:1.0: 4 ports detected
Nov 12 19:22:04 zion-desktop kernel: [   27.797051] Floppy drive(s): fd0 is 1.44M
Nov 12 19:22:04 zion-desktop kernel: [   27.820317] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Nov 12 19:22:04 zion-desktop kernel: [   27.820325] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 21 (level, high) -> IRQ 18
Nov 12 19:22:04 zion-desktop kernel: [   27.820338] ehci_hcd 0000:00:02.2: EHCI Host Controller
Nov 12 19:22:04 zion-desktop kernel: [   27.820363] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Nov 12 19:22:04 zion-desktop kernel: [   27.820388] ehci_hcd 0000:00:02.2: debug port 1
Nov 12 19:22:04 zion-desktop kernel: [   27.820399] ehci_hcd 0000:00:02.2: irq 18, io mem 0xfc004000
Nov 12 19:22:04 zion-desktop kernel: [   27.827941] FDC 0 is a post-1991 82077
Nov 12 19:22:04 zion-desktop kernel: [   27.963765] usb 1-1: new low speed USB device using ohci_hcd and address 2
Nov 12 19:22:04 zion-desktop kernel: [   27.963782] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 12 19:22:04 zion-desktop kernel: [   27.963874] usb usb3: configuration #1 chosen from 1 choice
Nov 12 19:22:04 zion-desktop kernel: [   27.963899] hub 3-0:1.0: USB hub found
Nov 12 19:22:04 zion-desktop kernel: [   27.963906] hub 3-0:1.0: 8 ports detected
Nov 12 19:22:04 zion-desktop kernel: [   28.067898] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
Nov 12 19:22:04 zion-desktop kernel: [   28.067980] NFORCE3-250: chipset revision 162
Nov 12 19:22:04 zion-desktop kernel: [   28.067982] NFORCE3-250: not 100%% native mode: will probe irqs later
Nov 12 19:22:04 zion-desktop kernel: [   28.067988] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
Nov 12 19:22:04 zion-desktop kernel: [   28.067995]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Nov 12 19:22:04 zion-desktop kernel: [   28.068003]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Nov 12 19:22:04 zion-desktop kernel: [   28.644528] usb 1-1: new low speed USB device using ohci_hcd and address 3
Nov 12 19:22:04 zion-desktop kernel: [   28.855925] usb 1-1: configuration #1 chosen from 1 choice
Nov 12 19:22:04 zion-desktop kernel: [   28.874484] usbcore: registered new interface driver hiddev
Nov 12 19:22:04 zion-desktop kernel: [   28.880104] input: A4Tech RF USB Mouse as /class/input/input2
Nov 12 19:22:04 zion-desktop kernel: [   28.880222] input: USB HID v1.10 Mouse [A4Tech RF USB Mouse] on usb-0000:00:02.0-1
Nov 12 19:22:04 zion-desktop kernel: [   28.880234] usbcore: registered new interface driver usbhid
Nov 12 19:22:04 zion-desktop kernel: [   28.880238] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov 12 19:22:04 zion-desktop kernel: [   29.371448] hdc: TSSTcorpCD/DVDW SH-S182M, ATAPI CD/DVD-ROM drive
Nov 12 19:22:04 zion-desktop kernel: [   30.043889] ide1 at 0x170-0x177,0x376 on irq 15
Nov 12 19:22:04 zion-desktop kernel: [   30.051302] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
Nov 12 19:22:04 zion-desktop kernel: [   30.051308] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [APSI] -> GSI 20 (level, high) -> IRQ 19
Nov 12 19:22:04 zion-desktop kernel: [   30.051392] scsi0 : sata_nv
Nov 12 19:22:04 zion-desktop kernel: [   30.051597] scsi1 : sata_nv
Nov 12 19:22:04 zion-desktop kernel: [   30.051749] ata1: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001c800 irq 19
Nov 12 19:22:04 zion-desktop kernel: [   30.051752] ata2: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001c808 irq 19
Nov 12 19:22:04 zion-desktop kernel: [   30.065697] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov 12 19:22:04 zion-desktop kernel: [   30.065705] Uniform CD-ROM driver Revision: 3.20
Nov 12 19:22:04 zion-desktop kernel: [   30.519068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 12 19:22:04 zion-desktop kernel: [   30.527266] ata1.00: ATA-6: ST3120827AS, 3.42, max UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   30.527269] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 12 19:22:04 zion-desktop kernel: [   30.543266] ata1.00: configured for UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   31.010936] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 12 19:22:04 zion-desktop kernel: [   31.057717] ata2.00: ATA-7: ST3200820AS, 3.AAD, max UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   31.057721] ata2.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 12 19:22:04 zion-desktop kernel: [   31.124327] ata2.00: configured for UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   31.124417] scsi 0:0:0:0: Direct-Access     ATA      ST3120827AS      3.42 PQ: 0 ANSI: 5
Nov 12 19:22:04 zion-desktop kernel: [   31.124780] scsi 1:0:0:0: Direct-Access     ATA      ST3200820AS      3.AA PQ: 0 ANSI: 5
Nov 12 19:22:04 zion-desktop kernel: [   31.125410] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
Nov 12 19:22:04 zion-desktop kernel: [   31.125413] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 23 (level, high) -> IRQ 16
Nov 12 19:22:04 zion-desktop kernel: [   31.125475] scsi2 : sata_nv
Nov 12 19:22:04 zion-desktop kernel: [   31.125617] scsi3 : sata_nv
Nov 12 19:22:04 zion-desktop kernel: [   31.125779] ata3: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 16
Nov 12 19:22:04 zion-desktop kernel: [   31.125782] ata4: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 16
Nov 12 19:22:04 zion-desktop kernel: [   31.590774] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 12 19:22:04 zion-desktop kernel: [   31.643284] ata3.00: ATA-7: ST3250824AS, 3.AAH, max UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   31.643288] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 12 19:22:04 zion-desktop kernel: [   31.709890] ata3.00: configured for UDMA/133
Nov 12 19:22:04 zion-desktop kernel: [   32.018649] ata4: SATA link down (SStatus 0 SControl 300)
Nov 12 19:22:04 zion-desktop kernel: [   32.018746] scsi 2:0:0:0: Direct-Access     ATA      ST3250824AS      3.AA PQ: 0 ANSI: 5
Nov 12 19:22:04 zion-desktop kernel: [   32.019415] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Nov 12 19:22:04 zion-desktop kernel: [   32.019422] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
Nov 12 19:22:04 zion-desktop kernel: [   32.072576] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fb001000-fb0017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 12 19:22:04 zion-desktop kernel: [   32.079646] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 12 19:22:04 zion-desktop kernel: [   32.079829] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Nov 12 19:22:04 zion-desktop kernel: [   32.079835] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
Nov 12 19:22:04 zion-desktop kernel: [   32.080113] eth0: RTL8110s at 0xf883c000, 00:11:09:dd:b9:8f, XID 04000000 IRQ 21
Nov 12 19:22:04 zion-desktop kernel: [   32.098653] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.101609] sd 0:0:0:0: [sda] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.106637] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.106735] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.106759] sd 0:0:0:0: [sda] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.106778] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.106782]  sda: sda1 sda2 < sda5 >
Nov 12 19:22:04 zion-desktop kernel: [   32.141082] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 12 19:22:04 zion-desktop kernel: [   32.141739] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.141750] sd 1:0:0:0: [sdb] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.141765] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.141802] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.141810] sd 1:0:0:0: [sdb] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.141825] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.141828]  sdb: sdb1
Nov 12 19:22:04 zion-desktop kernel: [   32.155038] sd 1:0:0:0: [sdb] Attached SCSI disk
Nov 12 19:22:04 zion-desktop kernel: [   32.155402] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.155410] sd 2:0:0:0: [sdc] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.155424] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.155452] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:22:04 zion-desktop kernel: [   32.155460] sd 2:0:0:0: [sdc] Write Protect is off
Nov 12 19:22:04 zion-desktop kernel: [   32.155474] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 12 19:22:04 zion-desktop kernel: [   32.155477]  sdc: sdc1
Nov 12 19:22:04 zion-desktop kernel: [   32.174316] sd 2:0:0:0: [sdc] Attached SCSI disk
Nov 12 19:22:04 zion-desktop kernel: [   32.177978] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 12 19:22:04 zion-desktop kernel: [   32.177996] sd 1:0:0:0: Attached scsi generic sg1 type 0
Nov 12 19:22:04 zion-desktop kernel: [   32.178013] sd 2:0:0:0: Attached scsi generic sg2 type 0
Nov 12 19:22:04 zion-desktop kernel: [   32.451299] Attempting manual resume
Nov 12 19:22:04 zion-desktop kernel: [   32.487174] kjournald starting.  Commit interval 5 seconds
Nov 12 19:22:04 zion-desktop kernel: [   32.487184] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 19:22:04 zion-desktop kernel: [   38.784360] r8169: eth0: link up
Nov 12 19:22:04 zion-desktop kernel: [   40.182004] Linux agpgart interface v0.102 (c) Dave Jones
Nov 12 19:22:04 zion-desktop kernel: [   40.191060] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Nov 12 19:22:04 zion-desktop kernel: [   40.191086] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Nov 12 19:22:04 zion-desktop kernel: [   40.199972] agpgart: Detected AGP bridge 0
Nov 12 19:22:04 zion-desktop kernel: [   40.199986] agpgart: Setting up Nforce3 AGP.
Nov 12 19:22:04 zion-desktop kernel: [   40.203682] agpgart: AGP aperture is 128M @ 0xf0000000
Nov 12 19:22:04 zion-desktop kernel: [   40.865358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 12 19:22:04 zion-desktop kernel: [   40.867562] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 12 19:22:04 zion-desktop kernel: [   41.508031] input: PC Speaker as /class/input/input3
Nov 12 19:22:04 zion-desktop kernel: [   41.657278] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 12 19:22:04 zion-desktop kernel: [   41.657323] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Nov 12 19:22:04 zion-desktop kernel: [   42.008605] nvidia: module license 'NVIDIA' taints kernel.
Nov 12 19:22:04 zion-desktop kernel: [   42.260599] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Nov 12 19:22:04 zion-desktop kernel: [   42.260603] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
Nov 12 19:22:04 zion-desktop kernel: [   42.260825] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
Nov 12 19:22:04 zion-desktop kernel: [   42.479052] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Nov 12 19:22:04 zion-desktop kernel: [   42.479056] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 22 (level, high) -> IRQ 17
Nov 12 19:22:04 zion-desktop kernel: [   42.799700] intel8x0_measure_ac97_clock: measured 54735 usecs
Nov 12 19:22:04 zion-desktop kernel: [   42.799703] intel8x0: clocking to 46916
Nov 12 19:22:04 zion-desktop kernel: [   43.368876] lp0: using parport0 (interrupt-driven).
Nov 12 19:22:04 zion-desktop kernel: [   43.447039] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
Nov 12 19:22:04 zion-desktop kernel: [   43.697620] EXT3 FS on sda1, internal journal
Nov 12 19:22:04 zion-desktop kernel: [   43.976874] kjournald starting.  Commit interval 5 seconds
Nov 12 19:22:04 zion-desktop kernel: [   43.976883] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Nov 12 19:22:04 zion-desktop kernel: [   43.983479] EXT3 FS on sdb1, internal journal
Nov 12 19:22:04 zion-desktop kernel: [   43.983483] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 19:22:04 zion-desktop kernel: [   44.017693] kjournald starting.  Commit interval 5 seconds
Nov 12 19:22:04 zion-desktop kernel: [   44.017699] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Nov 12 19:22:04 zion-desktop kernel: [   44.023467] EXT3 FS on sdc1, internal journal
Nov 12 19:22:04 zion-desktop kernel: [   44.023471] EXT3-fs: mounted filesystem with ordered data mode.
Nov 12 19:22:04 zion-desktop kernel: [   45.105263] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
Nov 12 19:22:04 zion-desktop kernel: [   45.287569] input: Power Button (FF) as /class/input/input4
Nov 12 19:22:04 zion-desktop kernel: [   45.291730] ACPI: Power Button (FF) [PWRF]
Nov 12 19:22:04 zion-desktop kernel: [   45.338016] input: Power Button (CM) as /class/input/input5
Nov 12 19:22:04 zion-desktop kernel: [   45.342229] ACPI: Power Button (CM) [PWRB]
Nov 12 19:22:04 zion-desktop kernel: [   45.418183] No dock devices found.
Nov 12 19:22:04 zion-desktop kernel: [   45.587784] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
Nov 12 19:22:05 zion-desktop kernel: [   46.981040] NET: Registered protocol family 10
Nov 12 19:22:05 zion-desktop kernel: [   46.981123] lo: Disabled Privacy Extensions
Nov 12 19:22:06 zion-desktop kernel: [   47.446153] ppdev: user-space parallel port driver
Nov 12 19:22:06 zion-desktop kernel: [   47.562091] audit(1194866526.230:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6410 profile="/usr/sbin/cupsd"
Nov 12 19:22:07 zion-desktop kernel: [   49.240341] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 12 19:22:07 zion-desktop kernel: [   49.240345] apm: overridden by ACPI.
Nov 12 19:22:08 zion-desktop kernel: [   50.225013] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Nov 12 19:22:10 zion-desktop kernel: [   51.352295] NET: Registered protocol family 17
Nov 12 19:22:10 zion-desktop kernel: [   52.149154] device eth0 entered promiscuous mode
Nov 12 19:22:10 zion-desktop kernel: [   52.149163] audit(1194866530.730:4): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov 12 19:22:10 zion-desktop kernel: [   52.161138] device eth0 left promiscuous mode
Nov 12 19:22:10 zion-desktop kernel: [   52.161143] audit(1194866530.730:5): dev=eth0 prom=0 old_prom=256 auid=4294967295
Nov 12 19:22:10 zion-desktop kernel: [   52.173143] device eth0 entered promiscuous mode
Nov 12 19:22:10 zion-desktop kernel: [   52.173153] audit(1194866530.730:6): dev=eth0 prom=256 old_prom=0 auid=4294967295
Nov 12 19:22:13 zion-desktop kernel: [   54.407390] Failure registering capabilities with primary security module.
Nov 12 19:22:13 zion-desktop dhcdbd: Started up.
Nov 12 19:22:16 zion-desktop kernel: [   57.930191] Bluetooth: Core ver 2.11
Nov 12 19:22:16 zion-desktop kernel: [   57.930332] NET: Registered protocol family 31
Nov 12 19:22:16 zion-desktop kernel: [   57.930334] Bluetooth: HCI device and connection manager initialized
Nov 12 19:22:16 zion-desktop kernel: [   57.930338] Bluetooth: HCI socket layer initialized
Nov 12 19:22:16 zion-desktop kernel: [   57.946774] Bluetooth: L2CAP ver 2.8
Nov 12 19:22:16 zion-desktop kernel: [   57.946778] Bluetooth: L2CAP socket layer initialized
Nov 12 19:22:16 zion-desktop kernel: [   58.033044] Bluetooth: RFCOMM socket layer initialized
Nov 12 19:22:16 zion-desktop kernel: [   58.033181] Bluetooth: RFCOMM TTY layer initialized
Nov 12 19:22:16 zion-desktop kernel: [   58.033183] Bluetooth: RFCOMM ver 1.8
Nov 12 19:22:20 zion-desktop kernel: [   61.142986] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Nov 12 19:22:20 zion-desktop kernel: [   61.143001] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Nov 12 19:22:20 zion-desktop kernel: [   61.143026] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Nov 12 19:23:36 zion-desktop kernel: [  137.730593] usb 3-7: new high speed USB device using ehci_hcd and address 3
Nov 12 19:23:37 zion-desktop kernel: [  138.810376] usb 3-7: new high speed USB device using ehci_hcd and address 4
Nov 12 19:23:39 zion-desktop kernel: [  140.857964] usb 3-7: new high speed USB device using ehci_hcd and address 5
Nov 12 19:23:42 zion-desktop kernel: [  143.393472] usb 3-7: new high speed USB device using ehci_hcd and address 6
Nov 12 19:24:16 zion-desktop kernel: [  177.750567] usb 3-8: new high speed USB device using ehci_hcd and address 7
Nov 12 19:24:17 zion-desktop kernel: [  178.746338] usb 3-8: new high speed USB device using ehci_hcd and address 8
Nov 12 19:24:17 zion-desktop kernel: [  179.135652] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:24:17 zion-desktop kernel: [  179.220614] usbcore: registered new interface driver libusual
Nov 12 19:24:18 zion-desktop kernel: [  179.246208] Initializing USB Mass Storage driver...
Nov 12 19:24:18 zion-desktop kernel: [  179.246406] scsi4 : SCSI emulation for USB Mass Storage devices
Nov 12 19:24:18 zion-desktop kernel: [  179.246835] usbcore: registered new interface driver usb-storage
Nov 12 19:24:18 zion-desktop kernel: [  179.246974] USB Mass Storage support registered.
Nov 12 19:24:23 zion-desktop kernel: [  184.245935] scsi 4:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:24:23 zion-desktop kernel: [  184.248120] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:24:23 zion-desktop kernel: [  184.248995] sd 4:0:0:0: [sdd] Write Protect is off
Nov 12 19:24:23 zion-desktop kernel: [  184.250118] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:24:23 zion-desktop kernel: [  184.250994] sd 4:0:0:0: [sdd] Write Protect is off
Nov 12 19:24:23 zion-desktop kernel: [  184.251001]  sdd: sdd1
Nov 12 19:24:23 zion-desktop kernel: [  184.273286] sd 4:0:0:0: [sdd] Attached SCSI disk
Nov 12 19:24:23 zion-desktop kernel: [  184.273324] sd 4:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:24:31 zion-desktop kernel: [  192.576382] usb 3-8: USB disconnect, address 8
Nov 12 19:24:31 zion-desktop kernel: [  192.847525] usb 3-8: new high speed USB device using ehci_hcd and address 9
Nov 12 19:24:32 zion-desktop kernel: [  193.232793] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:24:32 zion-desktop kernel: [  193.233042] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 12 19:24:33 zion-desktop kernel: [  195.078604] usb 3-8: USB disconnect, address 9
Nov 12 19:24:34 zion-desktop kernel: [  195.346998] usb 3-8: new high speed USB device using ehci_hcd and address 10
Nov 12 19:24:34 zion-desktop kernel: [  195.740391] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:24:34 zion-desktop kernel: [  195.740641] scsi6 : SCSI emulation for USB Mass Storage devices
Nov 12 19:24:34 zion-desktop kernel: [  195.769091] usb 3-8: USB disconnect, address 10
Nov 12 19:24:51 zion-desktop kernel: [  212.907464] usb 3-8: new high speed USB device using ehci_hcd and address 11
Nov 12 19:24:52 zion-desktop kernel: [  213.899263] usb 3-8: new high speed USB device using ehci_hcd and address 12
Nov 12 19:24:53 zion-desktop kernel: [  214.292657] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:24:53 zion-desktop kernel: [  214.292903] scsi7 : SCSI emulation for USB Mass Storage devices
Nov 12 19:24:58 zion-desktop kernel: [  219.290791] scsi 7:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:24:58 zion-desktop kernel: [  219.292522] sd 7:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:24:58 zion-desktop kernel: [  219.293397] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:24:58 zion-desktop kernel: [  219.294395] sd 7:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:24:58 zion-desktop kernel: [  219.295270] sd 7:0:0:0: [sdd] Write Protect is off
Nov 12 19:24:58 zion-desktop kernel: [  219.295278]  sdd: sdd1
Nov 12 19:24:58 zion-desktop kernel: [  219.320321] sd 7:0:0:0: [sdd] Attached SCSI disk
Nov 12 19:24:58 zion-desktop kernel: [  219.320355] sd 7:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:25:12 zion-desktop kernel: [  233.802221] usb 3-8: USB disconnect, address 12
Nov 12 19:25:12 zion-desktop kernel: [  234.075212] usb 3-8: new high speed USB device using ehci_hcd and address 13
Nov 12 19:25:13 zion-desktop kernel: [  234.460511] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:25:13 zion-desktop kernel: [  234.460757] scsi8 : SCSI emulation for USB Mass Storage devices
Nov 12 19:25:17 zion-desktop kernel: [  238.609707] usb 3-8: USB disconnect, address 13
Nov 12 19:25:17 zion-desktop kernel: [  238.878237] usb 3-8: new high speed USB device using ehci_hcd and address 14
Nov 12 19:25:18 zion-desktop kernel: [  239.263622] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:25:18 zion-desktop kernel: [  239.263869] scsi9 : SCSI emulation for USB Mass Storage devices
Nov 12 19:25:23 zion-desktop kernel: [  244.261779] scsi 9:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:25:23 zion-desktop kernel: [  244.263989] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:25:23 zion-desktop kernel: [  244.264863] sd 9:0:0:0: [sdd] Write Protect is off
Nov 12 19:25:23 zion-desktop kernel: [  244.265986] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:25:23 zion-desktop kernel: [  244.266861] sd 9:0:0:0: [sdd] Write Protect is off
Nov 12 19:25:23 zion-desktop kernel: [  244.266869]  sdd: sdd1
Nov 12 19:25:23 zion-desktop kernel: [  244.292037] sd 9:0:0:0: [sdd] Attached SCSI disk
Nov 12 19:25:23 zion-desktop kernel: [  244.292074] sd 9:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:26:15 zion-desktop kernel: [  296.722139] usb 3-8: USB disconnect, address 14
Nov 12 19:26:15 zion-desktop kernel: [  296.725446] sd 9:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:26:15 zion-desktop kernel: [  296.725460] lost page write due to I/O error on sdd1
Nov 12 19:26:15 zion-desktop kernel: [  296.725467] lost page write due to I/O error on sdd1
Nov 12 19:26:15 zion-desktop kernel: [  296.725472] lost page write due to I/O error on sdd1
Nov 12 19:26:15 zion-desktop kernel: [  296.725477] lost page write due to I/O error on sdd1
Nov 12 19:26:15 zion-desktop kernel: [  296.727514] sd 9:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 12 19:26:15 zion-desktop kernel: [  296.994551] usb 3-8: new high speed USB device using ehci_hcd and address 15
Nov 12 19:26:16 zion-desktop kernel: [  297.459910] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:26:16 zion-desktop kernel: [  297.460155] scsi10 : SCSI emulation for USB Mass Storage devices
Nov 12 19:26:21 zion-desktop kernel: [  302.458043] scsi 10:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:26:21 zion-desktop kernel: [  302.459774] sd 10:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:21 zion-desktop kernel: [  302.460399] sd 10:0:0:0: [sde] Write Protect is off
Nov 12 19:26:21 zion-desktop kernel: [  302.461449] sd 10:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:21 zion-desktop kernel: [  302.462272] sd 10:0:0:0: [sde] Write Protect is off
Nov 12 19:26:21 zion-desktop kernel: [  302.462280]  sde: sde1
Nov 12 19:26:21 zion-desktop kernel: [  302.487325] sd 10:0:0:0: [sde] Attached SCSI disk
Nov 12 19:26:21 zion-desktop kernel: [  302.487362] sd 10:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:26:21 zion-desktop kernel: [  302.750694] usb 3-8: USB disconnect, address 15
Nov 12 19:26:21 zion-desktop kernel: [  303.021328] usb 3-8: new high speed USB device using ehci_hcd and address 16
Nov 12 19:26:22 zion-desktop kernel: [  303.410659] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:26:22 zion-desktop kernel: [  303.410903] scsi11 : SCSI emulation for USB Mass Storage devices
Nov 12 19:26:26 zion-desktop kernel: [  307.426129] usb 3-8: USB disconnect, address 16
Nov 12 19:26:26 zion-desktop kernel: [  307.696398] usb 3-8: new high speed USB device using ehci_hcd and address 17
Nov 12 19:26:26 zion-desktop kernel: [  308.081673] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:26:26 zion-desktop kernel: [  308.081919] scsi12 : SCSI emulation for USB Mass Storage devices
Nov 12 19:26:31 zion-desktop kernel: [  313.079996] scsi 12:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:26:31 zion-desktop kernel: [  313.082038] sd 12:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:31 zion-desktop kernel: [  313.082910] sd 12:0:0:0: [sde] Write Protect is off
Nov 12 19:26:31 zion-desktop kernel: [  313.083673] sd 12:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:31 zion-desktop kernel: [  313.084534] sd 12:0:0:0: [sde] Write Protect is off
Nov 12 19:26:31 zion-desktop kernel: [  313.084542]  sde: sde1
Nov 12 19:26:31 zion-desktop kernel: [  313.112214] sd 12:0:0:0: [sde] Attached SCSI disk
Nov 12 19:26:31 zion-desktop kernel: [  313.112251] sd 12:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:26:41 zion-desktop kernel: [  322.633413] usb 3-8: USB disconnect, address 17
Nov 12 19:26:41 zion-desktop kernel: [  322.905342] usb 3-8: new high speed USB device using ehci_hcd and address 18
Nov 12 19:26:42 zion-desktop kernel: [  323.286704] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:26:42 zion-desktop kernel: [  323.286951] scsi13 : SCSI emulation for USB Mass Storage devices
Nov 12 19:26:47 zion-desktop kernel: [  328.284836] scsi 13:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:26:47 zion-desktop kernel: [  328.286566] sd 13:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:47 zion-desktop kernel: [  328.287441] sd 13:0:0:0: [sde] Write Protect is off
Nov 12 19:26:47 zion-desktop kernel: [  328.288440] sd 13:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:26:47 zion-desktop kernel: [  328.289065] sd 13:0:0:0: [sde] Write Protect is off
Nov 12 19:26:47 zion-desktop kernel: [  328.289073]  sde: sde1
Nov 12 19:26:47 zion-desktop kernel: [  328.316867] sd 13:0:0:0: [sde] Attached SCSI disk
Nov 12 19:26:47 zion-desktop kernel: [  328.316904] sd 13:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:26:53 zion-desktop kernel: [  335.060785] usb 3-8: USB disconnect, address 18
Nov 12 19:27:47 zion-desktop kernel: [  388.936036] usb 3-8: new high speed USB device using ehci_hcd and address 19
Nov 12 19:27:48 zion-desktop kernel: [  389.317437] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:27:48 zion-desktop kernel: [  389.317683] scsi14 : SCSI emulation for USB Mass Storage devices
Nov 12 19:27:53 zion-desktop kernel: [  394.315570] scsi 14:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:27:53 zion-desktop kernel: [  394.317301] sd 14:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:27:53 zion-desktop kernel: [  394.318176] sd 14:0:0:0: [sde] Write Protect is off
Nov 12 19:27:53 zion-desktop kernel: [  394.319174] sd 14:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:27:53 zion-desktop kernel: [  394.320050] sd 14:0:0:0: [sde] Write Protect is off
Nov 12 19:27:53 zion-desktop kernel: [  394.320057]  sde: sde1
Nov 12 19:27:53 zion-desktop kernel: [  394.347603] sd 14:0:0:0: [sde] Attached SCSI disk
Nov 12 19:27:53 zion-desktop kernel: [  394.347640] sd 14:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:27:54 zion-desktop kernel: [  395.464842] usb 3-8: USB disconnect, address 19
Nov 12 19:27:54 zion-desktop kernel: [  395.738680] usb 3-8: new high speed USB device using ehci_hcd and address 20
Nov 12 19:27:54 zion-desktop kernel: [  396.131995] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:27:54 zion-desktop kernel: [  396.132236] scsi15 : SCSI emulation for USB Mass Storage devices
Nov 12 19:27:59 zion-desktop kernel: [  401.130255] scsi 15:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:27:59 zion-desktop kernel: [  401.131986] sd 15:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:27:59 zion-desktop kernel: [  401.132861] sd 15:0:0:0: [sde] Write Protect is off
Nov 12 19:27:59 zion-desktop kernel: [  401.133860] sd 15:0:0:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:27:59 zion-desktop kernel: [  401.134734] sd 15:0:0:0: [sde] Write Protect is off
Nov 12 19:27:59 zion-desktop kernel: [  401.134742]  sde: sde1
Nov 12 19:27:59 zion-desktop kernel: [  401.158786] sd 15:0:0:0: [sde] Attached SCSI disk
Nov 12 19:27:59 zion-desktop kernel: [  401.158822] sd 15:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:28:29 zion-desktop kernel: [  430.542520] usb 3-8: USB disconnect, address 20
Nov 12 19:28:29 zion-desktop kernel: [  430.542755] printk: 10932 messages suppressed.
Nov 12 19:28:29 zion-desktop kernel: [  430.542761] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542768] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542774] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542779] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542784] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542945] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542950] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542955] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542960] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.542965] lost page write due to I/O error on sde1
Nov 12 19:28:29 zion-desktop kernel: [  430.803630] usb 3-8: new high speed USB device using ehci_hcd and address 21
Nov 12 19:28:30 zion-desktop kernel: [  431.192936] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:28:30 zion-desktop kernel: [  431.193180] scsi16 : SCSI emulation for USB Mass Storage devices
Nov 12 19:28:31 zion-desktop kernel: [  433.058487] usb 3-8: USB disconnect, address 21
Nov 12 19:28:32 zion-desktop kernel: [  433.327102] usb 3-8: new high speed USB device using ehci_hcd and address 22
Nov 12 19:42:04 zion-desktop -- MARK --
Nov 12 19:43:28 zion-desktop kernel: [ 1329.948744] nfs: server 192.168.0.200 not responding, still trying
Nov 12 19:51:50 zion-desktop kernel: [ 1831.827453] usb 3-8: new high speed USB device using ehci_hcd and address 24
Nov 12 19:51:55 zion-desktop kernel: [ 1836.064053] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:51:55 zion-desktop kernel: [ 1836.064301] scsi17 : SCSI emulation for USB Mass Storage devices
Nov 12 19:52:05 zion-desktop kernel: [ 1846.672705] usb 3-8: reset high speed USB device using ehci_hcd and address 24
Nov 12 19:52:06 zion-desktop kernel: [ 1847.939407] scsi 17:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:52:07 zion-desktop kernel: [ 1847.944486] sd 17:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:52:07 zion-desktop kernel: [ 1847.945197] sd 17:0:0:0: [sdf] Write Protect is off
Nov 12 19:52:07 zion-desktop kernel: [ 1847.945948] sd 17:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:52:07 zion-desktop kernel: [ 1847.946820] sd 17:0:0:0: [sdf] Write Protect is off
Nov 12 19:52:07 zion-desktop kernel: [ 1847.946828]  sdf: sdf1
Nov 12 19:52:07 zion-desktop kernel: [ 1847.971503] sd 17:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:52:07 zion-desktop kernel: [ 1847.971540] sd 17:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:53:36 zion-desktop kernel: [ 1937.129778] usb 3-8: USB disconnect, address 24
Nov 12 19:53:36 zion-desktop kernel: [ 1937.399878] usb 3-8: new high speed USB device using ehci_hcd and address 25
Nov 12 19:53:37 zion-desktop kernel: [ 1938.503688] usb 3-8: new high speed USB device using ehci_hcd and address 26
Nov 12 19:53:38 zion-desktop kernel: [ 1939.781054] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:53:38 zion-desktop kernel: [ 1939.781300] scsi18 : SCSI emulation for USB Mass Storage devices
Nov 12 19:53:43 zion-desktop kernel: [ 1944.779194] scsi 18:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:53:43 zion-desktop kernel: [ 1944.781048] sd 18:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:53:43 zion-desktop kernel: [ 1944.781923] sd 18:0:0:0: [sdf] Write Protect is off
Nov 12 19:53:43 zion-desktop kernel: [ 1944.782798] sd 18:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:53:43 zion-desktop kernel: [ 1944.783672] sd 18:0:0:0: [sdf] Write Protect is off
Nov 12 19:53:43 zion-desktop kernel: [ 1944.783680]  sdf: sdf1
Nov 12 19:53:43 zion-desktop kernel: [ 1944.808871] sd 18:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:53:43 zion-desktop kernel: [ 1944.808910] sd 18:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:53:54 zion-desktop kernel: [ 1955.623163] usb 3-8: USB disconnect, address 26
Nov 12 19:53:54 zion-desktop kernel: [ 1955.892436] usb 3-8: new high speed USB device using ehci_hcd and address 27
Nov 12 19:54:36 zion-desktop kernel: [ 1997.456707] usb 3-8: new high speed USB device using ehci_hcd and address 28
Nov 12 19:54:37 zion-desktop kernel: [ 1998.576502] usb 3-8: new high speed USB device using ehci_hcd and address 29
Nov 12 19:54:38 zion-desktop kernel: [ 1999.849694] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:54:38 zion-desktop kernel: [ 1999.854353] scsi19 : SCSI emulation for USB Mass Storage devices
Nov 12 19:54:43 zion-desktop kernel: [ 2004.851949] scsi 19:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:54:43 zion-desktop kernel: [ 2004.853681] sd 19:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:54:43 zion-desktop kernel: [ 2004.854555] sd 19:0:0:0: [sdf] Write Protect is off
Nov 12 19:54:43 zion-desktop kernel: [ 2004.855305] sd 19:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:54:43 zion-desktop kernel: [ 2004.856054] sd 19:0:0:0: [sdf] Write Protect is off
Nov 12 19:54:43 zion-desktop kernel: [ 2004.856062]  sdf: sdf1
Nov 12 19:54:43 zion-desktop kernel: [ 2004.876615] sd 19:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:54:43 zion-desktop kernel: [ 2004.876654] sd 19:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:54:48 zion-desktop kernel: [ 2008.991958] usb 3-8: USB disconnect, address 29
Nov 12 19:54:48 zion-desktop kernel: [ 2009.266512] usb 3-8: new high speed USB device using ehci_hcd and address 30
Nov 12 19:54:49 zion-desktop kernel: [ 2010.539713] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:54:49 zion-desktop kernel: [ 2010.539958] scsi20 : SCSI emulation for USB Mass Storage devices
Nov 12 19:54:50 zion-desktop kernel: [ 2011.115039] usb 3-8: USB disconnect, address 30
Nov 12 19:54:50 zion-desktop kernel: [ 2011.386129] usb 3-8: new high speed USB device using ehci_hcd and address 31
Nov 12 19:54:51 zion-desktop kernel: [ 2012.645891] usb 3-8: new high speed USB device using ehci_hcd and address 32
Nov 12 19:54:53 zion-desktop kernel: [ 2013.903059] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:54:53 zion-desktop kernel: [ 2013.983197] scsi21 : SCSI emulation for USB Mass Storage devices
Nov 12 19:54:58 zion-desktop kernel: [ 2018.981422] scsi 21:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:54:58 zion-desktop kernel: [ 2018.983153] sd 21:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:54:58 zion-desktop kernel: [ 2018.984028] sd 21:0:0:0: [sdf] Write Protect is off
Nov 12 19:54:58 zion-desktop kernel: [ 2018.984778] sd 21:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:54:58 zion-desktop kernel: [ 2018.985527] sd 21:0:0:0: [sdf] Write Protect is off
Nov 12 19:54:58 zion-desktop kernel: [ 2018.985535]  sdf: sdf1
Nov 12 19:54:58 zion-desktop kernel: [ 2019.006842] sd 21:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:54:58 zion-desktop kernel: [ 2019.006881] sd 21:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:55:05 zion-desktop kernel: [ 2026.298878] usb 3-8: USB disconnect, address 32
Nov 12 19:55:05 zion-desktop kernel: [ 2026.579346] usb 3-8: new high speed USB device using ehci_hcd and address 33
Nov 12 19:55:06 zion-desktop kernel: [ 2027.848511] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:55:06 zion-desktop kernel: [ 2027.848756] scsi22 : SCSI emulation for USB Mass Storage devices
Nov 12 19:55:11 zion-desktop kernel: [ 2032.846892] scsi 22:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:55:11 zion-desktop kernel: [ 2032.848623] sd 22:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:55:11 zion-desktop kernel: [ 2032.849498] sd 22:0:0:0: [sdf] Write Protect is off
Nov 12 19:55:11 zion-desktop kernel: [ 2032.850497] sd 22:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:55:11 zion-desktop kernel: [ 2032.851374] sd 22:0:0:0: [sdf] Write Protect is off
Nov 12 19:55:11 zion-desktop kernel: [ 2032.851383]  sdf: sdf1
Nov 12 19:55:11 zion-desktop kernel: [ 2032.878815] sd 22:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:55:11 zion-desktop kernel: [ 2032.878856] sd 22:0:0:0: Attached scsi generic sg3 type 0
Nov 12 19:55:16 zion-desktop kernel: [ 2037.635388] usb 3-8: USB disconnect, address 33
Nov 12 19:55:17 zion-desktop kernel: [ 2037.909271] usb 3-8: new high speed USB device using ehci_hcd and address 34
Nov 12 19:55:43 zion-desktop kernel: [ 2064.788349] usb 3-8: new high speed USB device using ehci_hcd and address 36
Nov 12 19:55:48 zion-desktop kernel: [ 2069.025050] usb 3-8: configuration #1 chosen from 1 choice
Nov 12 19:55:48 zion-desktop kernel: [ 2069.025291] scsi23 : SCSI emulation for USB Mass Storage devices
Nov 12 19:55:58 zion-desktop kernel: [ 2079.633626] usb 3-8: reset high speed USB device using ehci_hcd and address 36
Nov 12 19:56:00 zion-desktop kernel: [ 2080.901425] scsi 23:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
Nov 12 19:56:00 zion-desktop kernel: [ 2080.908892] sd 23:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:56:00 zion-desktop kernel: [ 2080.909770] sd 23:0:0:0: [sdf] Write Protect is off
Nov 12 19:56:00 zion-desktop kernel: [ 2080.911019] sd 23:0:0:0: [sdf] 488397168 512-byte hardware sectors (250059 MB)
Nov 12 19:56:00 zion-desktop kernel: [ 2080.911893] sd 23:0:0:0: [sdf] Write Protect is off
Nov 12 19:56:00 zion-desktop kernel: [ 2080.911901]  sdf: sdf1
Nov 12 19:56:00 zion-desktop kernel: [ 2080.939455] sd 23:0:0:0: [sdf] Attached SCSI disk
Nov 12 19:56:00 zion-desktop kernel: [ 2080.939491] sd 23:0:0:0: Attached scsi generic sg3 type 0
Nov 12 20:01:07 zion-desktop kernel: [ 2388.613364] usb 3-8: USB disconnect, address 36

This is the log as it was during the hour that I was trying it out.
I dont think that it is a hardware issue, at least not the Enclosure because Im using it at the
moment in Vista.  Although maybe theres something wrong with the USB port of my Ubuntu
machine.

---

### Post by worty on 2007-11-16
I have no idea about how the way linux handles USB but it might be a USB autosuspend issue. Here's a discussion thread that talks about it. It's mostly related to all USB-parallel adapter problems for printers that people are also having (me included) but it could be what's causing your problems as well. I haven't had much time recently to look into it myself but it might help you along in the right direction. [Link]("http://www.nabble.com/USB-Problems-with-Ubuntu---workaround-t4260039.html")

---

### Post by delphiguy on 2007-11-20
thanks for the help worty, i'll check it out now.

---

