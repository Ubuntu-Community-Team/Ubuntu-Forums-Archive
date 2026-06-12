---
title: "Having trouble getting my iPod to mount at all"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-05-01
Hey all! I am having some trouble getting my 5th gen. 30GB iPod to even mount. Every time I plug it in, I get this error:

```
Unable to mount volume IPOD. mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

Any idea what is causing this?

---

### Post by viciouslime on 2007-05-01
What's your ipod called? That's to say what have you set it's name to?

---

### Post by hackle577 on 2007-05-01
I tried to set it to "Adam's iPod" using Banshee or something, but now it wont mount at all so I can't find out.

---

### Post by Inxsible on 2007-05-01
Maybe the apostrophe is the problem. I am not very sure...but log into your Windows and change the name of your ipod to "Adam iPod" lets say and try again in Linux

---

### Post by nickj6282 on 2007-05-01
I have the same iPod named in Windows and OSX as "Nick's iPod" and it works fine under Ubuntu. Did you use iTunes to name your iPod? If you can, try connecting it to iTunes once and see what happens.

---

### Post by hackle577 on 2007-05-01
I don't dual boot, I only run Edgy. Could I use any copy of iTunes for this? Do I have to format it or something before I use it in Ubuntu?

---

### Post by nickj6282 on 2007-05-01
Yes. You can use any copy of iTunes. Just plug it in and see that iTunes recognizes it and use iTunes to rename it if you can.

If you have a friend or relative who has iTunes you can do that. Or school if you go to school. Otherwise you can always go into an Apple store, Best Buy, Fry's, Circuit City, or some similar place and use one of their computers for 30 seconds.

---

### Post by hackle577 on 2007-05-01
No dice. I am still getting the same error:

```
Unable to mount volume ADAM'S IPOD. mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```

Could it have something to do with the directory where Ubuntu is trying to mount it?

---

### Post by hackle577 on 2007-05-01
Output of "dmesg" with iPod connected:

```
[142377.056000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142491.916000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142501.552000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142624.792000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142748.128000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142789.408000] usb 1-1.1: new full speed USB device using uhci_hcd and address 16
[142789.536000] usb 1-1.1: configuration #1 chosen from 2 choices
[142789.540000] scsi13 : SCSI emulation for USB Mass Storage devices
[142789.540000] usb-storage: device found at 16
[142789.540000] usb-storage: waiting for device to settle before scanning
[142794.540000] usb-storage: device scan complete
[142794.544000] scsi 13:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[142794.552000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[142794.556000] sdb: Write Protect is off
[142794.556000] sdb: Mode Sense: 68 00 00 08
[142794.556000] sdb: assuming drive cache: write through
[142794.568000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[142794.572000] sdb: Write Protect is off
[142794.572000] sdb: Mode Sense: 68 00 00 08
[142794.572000] sdb: assuming drive cache: write through
[142794.572000]  sdb: sdb1 sdb2
[142794.592000] sd 13:0:0:0: Attached scsi removable disk sdb
[142794.592000] sd 13:0:0:0: Attached scsi generic sg2 type 0
[142871.536000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142965.888000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[142974.000000] usb 1-1.1: USB disconnect, address 16
[142995.428000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143118.744000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143243.088000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143316.872000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143366.960000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143490.216000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143520.848000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143613.424000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143731.852000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143736.632000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143860.068000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143983.940000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[143991.824000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144107.676000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144230.884000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144356.168000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144448.784000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144480.608000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144604.704000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144689.768000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144728.896000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144852.116000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144899.756000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[144975.332000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145098.544000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145211.736000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145221.756000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145344.988000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145468.232000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145552.716000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145591.448000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145714.660000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145837.872000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145925.696000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[145961.128000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146084.368000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146207.576000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146241.680000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146330.788000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146454.032000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146515.664000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146577.268000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146700.484000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146709.652000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146823.708000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146946.960000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[146981.636000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147070.196000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147193.420000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147316.632000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147426.608000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147439.880000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147563.096000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147615.600000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147686.280000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147809.536000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[147932.760000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148003.556000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148055.968000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148179.216000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148302.440000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148413.532000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148425.648000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148548.876000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148672.096000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148795.304000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148867.504000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[148918.548000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149041.760000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149164.976000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149229.484000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149288.232000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149411.444000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149486.464000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149534.652000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149657.960000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149781.316000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149836.456000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[149905.824000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150030.496000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150044.436000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150154.036000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150278.388000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150353.420000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150401.640000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150524.860000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150648.840000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150772.892000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150814.420000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[150896.368000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151019.608000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151143.148000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151266.420000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151279.336000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151389.672000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151512.896000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151613.320000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151636.588000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151759.844000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151883.092000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[151908.304000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152006.300000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152129.520000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152166.288000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152252.740000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152351.280000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152375.988000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152499.216000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152622.424000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152679.264000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152745.668000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152868.892000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[152992.100000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153115.328000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153137.236000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153238.560000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153358.216000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153361.772000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153484.992000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153608.224000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153701.208000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153731.456000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153854.688000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[153977.920000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154101.136000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154131.176000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154223.824000] usb 1-1.1: new full speed USB device using uhci_hcd and address 17
[154223.952000] usb 1-1.1: configuration #1 chosen from 2 choices
[154223.956000] scsi14 : SCSI emulation for USB Mass Storage devices
[154223.956000] usb-storage: device found at 17
[154223.956000] usb-storage: waiting for device to settle before scanning
[154224.356000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154228.956000] usb-storage: device scan complete
[154228.960000] scsi 14:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[154228.988000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[154228.996000] sdb: Write Protect is off
[154228.996000] sdb: Mode Sense: 68 00 00 08
[154228.996000] sdb: assuming drive cache: write through
[154229.008000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[154229.012000] sdb: Write Protect is off
[154229.012000] sdb: Mode Sense: 68 00 00 08
[154229.012000] sdb: assuming drive cache: write through
[154229.012000]  sdb: sdb1 sdb2
[154229.032000] sd 14:0:0:0: Attached scsi removable disk sdb
[154229.032000] sd 14:0:0:0: Attached scsi generic sg2 type 0
[154347.720000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154471.596000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154546.152000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154594.840000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154718.404000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154841.704000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154853.108000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[154885.208000] usb 1-1.1: USB disconnect, address 17
[154966.492000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155089.732000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155142.100000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155213.900000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155337.540000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155368.080000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155460.764000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155584.044000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155589.076000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155707.272000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155830.500000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155946.044000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[155954.568000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156077.936000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156201.964000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156264.032000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156325.236000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156448.460000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156571.700000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156694.916000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156740.000000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156818.132000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[156941.372000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157064.604000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157113.980000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157187.820000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157311.036000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157402.964000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157434.284000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157557.500000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157680.708000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157798.940000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157803.940000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[157927.164000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158050.640000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158173.920000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158174.920000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158298.136000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158421.440000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158545.508000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158573.872000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158669.372000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158793.076000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158912.860000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[158916.724000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159040.888000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159164.732000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159227.836000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159288.324000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159411.904000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159487.744000] usb 1-1.1: new full speed USB device using uhci_hcd and address 18
[159487.880000] usb 1-1.1: configuration #1 chosen from 2 choices
[159487.884000] scsi15 : SCSI emulation for USB Mass Storage devices
[159487.884000] usb-storage: device found at 18
[159487.884000] usb-storage: waiting for device to settle before scanning
[159492.884000] usb-storage: device scan complete
[159492.888000] scsi 15:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[159492.896000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159492.900000] sdb: Write Protect is off
[159492.900000] sdb: Mode Sense: 68 00 00 08
[159492.900000] sdb: assuming drive cache: write through
[159492.912000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159492.916000] sdb: Write Protect is off
[159492.916000] sdb: Mode Sense: 68 00 00 08
[159492.916000] sdb: assuming drive cache: write through
[159492.916000]  sdb: sdb1 sdb2
[159492.936000] sd 15:0:0:0: Attached scsi removable disk sdb
[159492.936000] sd 15:0:0:0: Attached scsi generic sg2 type 0
[159536.424000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159636.372000] usb 1-1.1: USB disconnect, address 18
[159651.292000] usb 1-1.1: new full speed USB device using uhci_hcd and address 19
[159651.420000] usb 1-1.1: configuration #1 chosen from 2 choices
[159651.424000] scsi16 : SCSI emulation for USB Mass Storage devices
[159651.424000] usb-storage: device found at 19
[159651.424000] usb-storage: waiting for device to settle before scanning
[159656.424000] usb-storage: device scan complete
[159656.428000] scsi 16:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[159656.436000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159656.444000] sdb: Write Protect is off
[159656.444000] sdb: Mode Sense: 68 00 00 08
[159656.444000] sdb: assuming drive cache: write through
[159656.452000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159656.456000] sdb: Write Protect is off
[159656.456000] sdb: Mode Sense: 68 00 00 08
[159656.456000] sdb: assuming drive cache: write through
[159656.456000]  sdb: sdb1 sdb2
[159656.472000] sd 16:0:0:0: Attached scsi removable disk sdb
[159656.472000] sd 16:0:0:0: Attached scsi generic sg2 type 0
[159660.964000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159694.812000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159784.692000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159870.176000] usb 1-1.1: USB disconnect, address 19
[159900.964000] usb 1-1.1: new full speed USB device using uhci_hcd and address 20
[159901.092000] usb 1-1.1: configuration #1 chosen from 2 choices
[159901.108000] scsi17 : SCSI emulation for USB Mass Storage devices
[159901.124000] usb-storage: device found at 20
[159901.124000] usb-storage: waiting for device to settle before scanning
[159906.124000] usb-storage: device scan complete
[159906.128000] scsi 17:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[159906.132000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159906.136000] sdb: Write Protect is off
[159906.136000] sdb: Mode Sense: 68 00 00 08
[159906.136000] sdb: assuming drive cache: write through
[159906.148000] SCSI device sdb: 14651280 2048-byte hdwr sectors (30006 MB)
[159906.152000] sdb: Write Protect is off
[159906.152000] sdb: Mode Sense: 68 00 00 08
[159906.152000] sdb: assuming drive cache: write through
[159906.152000]  sdb: sdb1 sdb2
[159906.164000] sd 17:0:0:0: Attached scsi removable disk sdb
[159906.164000] sd 17:0:0:0: Attached scsi generic sg2 type 0
[159908.432000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.
[159909.820000] bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed.

```

---

### Post by hackle577 on 2007-05-01
Hey-oh! Fixed it myself!

---

### Post by drmbogo on 2007-05-01
ok...how?

---

### Post by hackle577 on 2007-05-02
Well it turns out I had accidentally changed some of my iPod's settings. What I did was go into Nautilus and go to "Computer" then right click on the iPod icon, then tab over to "Drive" and "Volume" and erase all the mount options, etc. in both tabs. Worked fine after that!

---

### Post by sah18 on 2007-05-03
what did you do to fix it?  i'm having also with getting an ipod to mount (3G).  i was told that it should automount automatically, when it is connected via USB, is this correct??

---

### Post by hackle577 on 2007-05-03
Yeah, your iPod should mount autmatically. I'm afraid I'm no expert, I just happened upon the solution by chance, so if it is another problem I unfortunately can't help you.

---

### Post by trjnhrse44 on 2007-05-04
don't forget guys ipods must be formatted first throiugh either a windows or mac box as apple has not released the firmware updater for linux.  As long as the ipod has had music on it you should be fine, but if it is new it must be formatted before you use it with linux.  Sux I know but thank jobs for that

---

### Post by kordite on 2007-05-14
Now, my iPod was working properly in v6.06. I'm not sure whether it was upgrading to 7.04 or repartitioning the drive but it will not mount anymore. Plug it in and nothing.

---

### Post by kordite on 2007-06-04
I have solved my problem by connecting the external power supply to my USB hub. Apparently Ubuntu v6 is able to see the iPod with the onboard power but v7 needs more power to recognize that the USB device is even plugged in.

---

