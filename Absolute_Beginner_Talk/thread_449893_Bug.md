---
title: "Bug ?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-20
seems i have a bug (I think never came across one)

start up gives me a problem 
it runs 


[223.33783] ata 1: 0x0 Serr
 three lines but whole lines something like this , i'll make a picture 

20 min. before it starts up 

it stopped one day but now it seems like something forever 

i lke ubuntu , will not go back to my (e)x p :lolflag:, but do i really have to check another distro :(

i do everything until now 

bug had something to do with videocard if i'm not mistaking

---

### Post by firedancer on 2007-05-21
can anybody help with this ?? :confused:

or change to other distro 
working alrite , startup takes long with this info 

trying to check what video card i have 

but i'm new in this , but willing 


can i fix this or ..... like ubuntu until now but ......

mesdg

[  611.111416]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  611.119798] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  611.127780] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  611.127789] ata1.00: configured for UDMA/100
[  611.135762] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  611.135769] ata1.01: configured for UDMA/100
[  611.135790] ata1: EH complete
[  612.949844] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  612.949906] ata1.01: (BMDMA stat 0x65)
[  612.949960] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  612.949962]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  612.956872] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  612.964861] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  612.964866] ata1.00: configured for UDMA/100
[  612.972849] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  612.972853] ata1.01: configured for UDMA/100
[  612.972869] ata1: EH complete
[  612.987632] iTCO_vendor_support: vendor-support=0
[  614.795450] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  614.795513] ata1.01: (BMDMA stat 0x65)
[  614.795566] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  614.795568]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  614.802051] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  614.901829] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  614.901836] ata1.00: configured for UDMA/100
[  614.909862] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  614.909869] ata1.01: configured for UDMA/100
[  614.909890] ata1: EH complete
[  616.732497] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  616.732559] ata1.01: (BMDMA stat 0x65)
[  616.732613] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  616.732615]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  616.738940] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  616.906691] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  616.906699] ata1.00: configured for UDMA/100
[  616.914678] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  616.914682] ata1.01: configured for UDMA/100
[  616.914701] ata1: EH complete
[  618.831032] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  618.831095] ata1.01: (BMDMA stat 0x65)
[  618.831148] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  618.831150]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  618.839669] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  618.903567] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  618.903574] ata1.00: configured for UDMA/100
[  618.911553] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  618.911557] ata1.01: configured for UDMA/100
[  618.911581] sd 0:0:1:0: SCSI error: return code = 0x08000002
[  618.911584] sdb: Current [descriptor]: sense key: Medium Error
[  618.911588]     Additional sense: Unrecovered read error - auto reallocate failed
[  618.911594] Descriptor sense data with sense descriptors (in hex):
[  618.911597]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  618.911607]         00 00 00 08 
[  618.911612] end_request: I/O error, dev sdb, sector 8
[  618.911617] Buffer I/O error on device sdb, logical block 1
[  618.911698] ata1: EH complete
[  618.923041] sdb: Write Protect is off
[  618.923047] sdb: Mode Sense: 00 3a 00 00
[  620.939168] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  620.939229] ata1.01: (BMDMA stat 0x65)
[  620.939283] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  620.939284]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  620.948373] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  620.956368] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  620.956373] ata1.00: configured for UDMA/100
[  620.964341] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  620.964345] ata1.01: configured for UDMA/100
[  620.964361] ata1: EH complete
[  622.784767] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  622.784829] ata1.01: (BMDMA stat 0x65)
[  622.784883] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  622.784885]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  622.793491] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  622.905296] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  622.905303] ata1.00: configured for UDMA/100
[  622.913292] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  622.913296] ata1.01: configured for UDMA/100
[  622.913315] ata1: EH complete
[  624.730168] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  624.730231] ata1.01: (BMDMA stat 0x65)
[  624.730285] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  624.730286]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  624.738451] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  624.894192] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  624.894199] ata1.00: configured for UDMA/100
[  624.902217] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  624.902224] ata1.01: configured for UDMA/100
[  624.902243] ata1: EH complete
[  624.910081] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  624.911684] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[  624.912542] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  627.240804] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  627.240866] ata1.01: (BMDMA stat 0x65)
[  627.240920] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  627.240922]          res 51/40:08:0a:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  627.250508] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  627.258495] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  627.258500] ata1.00: configured for UDMA/100
[  627.266483] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  627.266487] ata1.01: configured for UDMA/100
[  627.266505] ata1: EH complete
[  629.189627] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  629.189689] ata1.01: (BMDMA stat 0x65)
[  629.189743] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  629.189745]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  629.199439] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  629.207441] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  629.207446] ata1.00: configured for UDMA/100
[  629.215465] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  629.215472] ata1.01: configured for UDMA/100
[  629.215491] ata1: EH complete
[  631.168253] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  631.168322] ata1.01: (BMDMA stat 0x65)
[  631.168376] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  631.168378]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  631.176365] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  631.184343] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  631.184348] ata1.00: configured for UDMA/100
[  631.192305] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  631.192309] ata1.01: configured for UDMA/100
[  631.192330] sd 0:0:1:0: SCSI error: return code = 0x08000002
[  631.192334] sdb: Current [descriptor]: sense key: Medium Error
[  631.192338]     Additional sense: Unrecovered read error - auto reallocate failed
[  631.192345] Descriptor sense data with sense descriptors (in hex):
[  631.192347]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  631.192357]         00 00 00 08 
[  631.192362] end_request: I/O error, dev sdb, sector 8
[  631.192367] Buffer I/O error on device sdb, logical block 1
[  631.192449] ata1: EH complete
[  631.211281] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  633.035349] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  633.035412] ata1.01: (BMDMA stat 0x65)
[  633.035465] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  633.035467]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  633.045415] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  633.053410] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  633.053415] ata1.00: configured for UDMA/100
[  633.061379] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  633.061383] ata1.01: configured for UDMA/100
[  633.061399] ata1: EH complete
[  634.914148] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  634.914211] ata1.01: (BMDMA stat 0x65)
[  634.914264] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  634.914266]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  634.922520] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  634.934504] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  634.934511] ata1.00: configured for UDMA/100
[  634.946459] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  634.946463] ata1.01: configured for UDMA/100
[  634.946484] ata1: EH complete
[  634.946587] SCSI device sda: 78156288 512-byte hdwr sectors (40016 MB)
[  636.798375] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  636.798439] ata1.01: (BMDMA stat 0x65)
[  636.798492] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  636.798494]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  636.807542] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  636.891400] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  636.891407] ata1.00: configured for UDMA/100
[  636.903396] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  636.903400] ata1.01: configured for UDMA/100
[  636.903420] ata1: EH complete
[  636.903523] sda: Write Protect is off
[  636.903528] sda: Mode Sense: 00 3a 00 00
[  638.762438] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  638.762500] ata1.01: (BMDMA stat 0x65)
[  638.762553] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  638.762555]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  638.772492] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  638.888295] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  638.888302] ata1.00: configured for UDMA/100
[  638.900288] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  638.900292] ata1.01: configured for UDMA/100
[  638.900313] ata1: EH complete
[  640.708712] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  640.708774] ata1.01: (BMDMA stat 0x65)
[  640.708827] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  640.708829]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  640.717428] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  640.729411] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  640.729416] ata1.00: configured for UDMA/100
[  640.741391] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  640.741395] ata1.01: configured for UDMA/100
[  640.741411] ata1: EH complete
[  640.741516] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  642.676883] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  642.676945] ata1.01: (BMDMA stat 0x65)
[  642.676999] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  642.677001]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  642.686348] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  642.698336] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  642.698342] ata1.00: configured for UDMA/100
[  642.710313] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  642.710318] ata1.01: configured for UDMA/100
[  642.710340] sd 0:0:1:0: SCSI error: return code = 0x08000002
[  642.710344] sdb: Current [descriptor]: sense key: Medium Error
[  642.710348]     Additional sense: Unrecovered read error - auto reallocate failed
[  642.710354] Descriptor sense data with sense descriptors (in hex):
[  642.710357]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  642.710367]         00 00 00 08 
[  642.710372] end_request: I/O error, dev sdb, sector 8
[  642.710376] Buffer I/O error on device sdb, logical block 1
[  642.710460] ata1: EH complete
[  642.729412] SCSI device sdb: 78156288 512-byte hdwr sectors (40016 MB)
[  642.738053] sdb: Write Protect is off
[  642.738058] sdb: Mode Sense: 00 3a 00 00
[  642.745670] Linux agpgart interface v0.102 (c) Dave Jones
[  644.548641] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  644.548704] ata1.01: (BMDMA stat 0x65)
[  644.548757] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  644.548759]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  644.559416] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  644.571395] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  644.571400] ata1.00: configured for UDMA/100
[  644.583360] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  644.583363] ata1.01: configured for UDMA/100
[  644.583379] ata1: EH complete
[  646.410920] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  646.410983] ata1.01: (BMDMA stat 0x65)
[  646.411036] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  646.411038]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  646.420526] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  646.432478] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  646.432483] ata1.00: configured for UDMA/100
[  646.444466] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  646.444471] ata1.01: configured for UDMA/100
[  646.444487] ata1: EH complete
[  648.454429] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  648.454492] ata1.01: (BMDMA stat 0x65)
[  648.454545] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  648.454547]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  648.465305] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  648.477302] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  648.477307] ata1.00: configured for UDMA/100
[  648.489273] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  648.489277] ata1.01: configured for UDMA/100
[  648.489292] ata1: EH complete
[  651.017494] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  651.017560] ata1.01: (BMDMA stat 0x65)
[  651.017614] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  651.017616]          res 51/40:08:0b:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  651.029276] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  651.041270] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  651.041275] ata1.00: configured for UDMA/100
[  651.053253] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  651.053257] ata1.01: configured for UDMA/100
[  651.053273] ata1: EH complete
[  653.053520] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  653.053583] ata1.01: (BMDMA stat 0x65)
[  653.053636] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  653.053639]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  653.062092] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  653.074064] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  653.074069] ata1.00: configured for UDMA/100
[  653.086091] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  653.086095] ata1.01: configured for UDMA/100
[  653.086111] ata1: EH complete
[  653.105906] agpgart: Detected an Intel 845G Chipset.
[  653.110463] agpgart: AGP aperture is 64M @ 0xf8000000
[  654.908222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  654.908285] ata1.01: (BMDMA stat 0x65)
[  654.908338] ata1.01: cmd c8/00:08:08:00:00/00:00:00:00:00/f0 tag 0 cdb 0x0 data 4096 in
[  654.908340]          res 51/40:08:08:00:00/00:00:00:00:00/f0 Emask 0x9 (media error)
[  654.919225] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  654.931168] ata1.00: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  654.931174] ata1.00: configured for UDMA/100
[  654.943153] ata1.01: ata_hpa_resize 1: sectors = 78156288, hpa_sectors = 78156288
[  654.943158] ata1.01: configured for UDMA/100
[  654.943184] sd 0:0:1:0: SCSI error: return code = 0x08000002
[  654.943188] sdb: Current [descriptor]: sense key: Medium Error
[  654.943192]     Additional sense: Unrecovered read error - auto reallocate failed
[  654.943198] Descriptor sense data with sense descriptors (in hex):
[  654.943201]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  654.943211]         00 00 00 08 
[  654.943216] end_request: I/O error, dev sdb, sector 8
[  654.943222] Buffer I/O error on device sdb, logical block 1
[  654.943306] ata1: EH complete
[  654.978411] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  657.563976] SCSI device sda: 78156288 512-byte hdwr sectors (40016 MB)
[  657.585595] sda: Write Protect is off
[  657.585602] sda: Mode Sense: 00 3a 00 00
[  657.585767] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  657.585831] SCSI device sdb: 78156288 512-byte hdwr sectors (40016 MB)
[  657.585855] sdb: Write Protect is off
[  657.585858] sdb: Mode Sense: 00 3a 00 00
[  657.585896] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  657.601633] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  657.654383] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  657.673716] input: PC Speaker as /class/input/input3
[  657.830270] usbcore: registered new interface driver xpad
[  657.830278] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[  657.844244] intel_rng: Firmware space is locked read-only. If you can't or
[  657.844248] intel_rng: don't want to disable this in firmware setup, and if
[  657.844249] intel_rng: you are certain that your system has a functional
[  657.844251] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  657.859541] fuse init (API version 7.8)
[  657.892648] lp0: using parport0 (interrupt-driven).
[  658.235236] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[  658.235288] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  658.240225] usbcore: registered new interface driver snd-usb-audio
[  658.356425] Adding 1646620k swap on /dev/disk/by-uuid/a881e468-b115-4f0f-b0f7-089ded561932.  Priority:-1 extents:1 across:1646620k
[  658.405783] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[  658.556338] intel8x0_measure_ac97_clock: measured 57982 usecs
[  658.556344] intel8x0: clocking to 48000
[  658.557565] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[  658.576560] gameport: ES1938 is pci0000:02:02.0/gameport0, io 0xd400, speed 946kHz
[  658.975426] EXT3 FS on sda1, internal journal
[  659.268716] NET: Registered protocol family 10
[  659.268903] lo: Disabled Privacy Extensions
[  666.268306] input: Power Button (FF) as /class/input/input5
[  666.268755] ACPI: Power Button (FF) [PWRF]
[  666.280287] input: Sleep Button (CM) as /class/input/input6
[  666.280741] ACPI: Sleep Button (CM) [SLPB]
[  666.362182] Using specific hotkey driver
[  666.552602] ibm_acpi: ec object not found
[  666.595268] No dock devices found.
[  666.708478] pcc_acpi: loading...
[  669.591033] eth0: no IPv6 routers present
[  673.264398] ppdev: user-space parallel port driver
[  673.454418] [drm] Initialized drm 1.1.0 20060810
[  673.498561] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  673.503467] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  676.222860] apm: BIOS not found.
[  676.769434] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  676.769464] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  676.769502] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  676.830575] Bluetooth: Core ver 2.11
[  676.861424] NET: Registered protocol family 31
[  676.861432] Bluetooth: HCI device and connection manager initialized
[  676.861437] Bluetooth: HCI socket layer initialized
[  676.882546] Bluetooth: L2CAP ver 2.8
[  676.882552] Bluetooth: L2CAP socket layer initialized
[  676.996043] Bluetooth: RFCOMM socket layer initialized
[  676.996449] Bluetooth: RFCOMM TTY layer initialized
[  676.996459] Bluetooth: RFCOMM ver 1.8
[  677.277767] [drm] Setting GART location based on new memory map
[  677.277837] [drm] writeback test succeeded in 1 usecs
[  687.139561] eth0: no IPv6 routers present
[10414.846448] mtrr: no MTRR for e8000000,4000000 found
[10415.256905] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[10415.256935] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[10415.256971] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[10415.815584] [drm] Setting GART location based on new memory map
[10415.815654] [drm] writeback test succeeded in 1 usecs
[30906.096756] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[30906.096786] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[30906.096821] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[35983.406853] usb 4-1: new high speed USB device using ehci_hcd and address 3
[35983.541475] usb 4-1: configuration #1 chosen from 1 choice
[35983.694121] usbcore: registered new interface driver libusual
[35983.712129] Initializing USB Mass Storage driver...
[35983.712294] scsi2 : SCSI emulation for USB Mass Storage devices
[35983.712437] usbcore: registered new interface driver usb-storage
[35983.712443] USB Mass Storage support registered.
[35983.712662] usb-storage: device found at 3
[35983.712666] usb-storage: waiting for device to settle before scanning
[35988.706709] usb-storage: device scan complete
[35988.707675] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[35989.645068] SCSI device sdc: 4030464 512-byte hdwr sectors (2064 MB)
[35989.645715] sdc: Write Protect is off
[35989.645723] sdc: Mode Sense: 23 00 00 00
[35989.645726] sdc: assuming drive cache: write through
[35989.648436] SCSI device sdc: 4030464 512-byte hdwr sectors (2064 MB)
[35989.649088] sdc: Write Protect is off
[35989.649097] sdc: Mode Sense: 23 00 00 00
[35989.649099] sdc: assuming drive cache: write through
[35989.649105]  sdc: sdc1
[35989.650261] sd 2:0:0:0: Attached scsi removable disk sdc
[35989.650349] sd 2:0:0:0: Attached scsi generic sg4 type 0
[50370.040558] lp0 out of paper
[50593.083503] lp0 out of paper
fayaman@dragon-desktop:~$

---

### Post by silent1643 on 2007-05-21
not sure, file a bug report on launchpad, look at the sticky post in this forum

---

### Post by firedancer on 2007-05-22
Ooops !

---

### Post by firedancer on 2007-05-23
is anybody there anybody , who can give me an answer:o

---

### Post by Terl on 2007-05-23
Can you run the following and post the output?  On the second one it is a small L

```
lspci
```

```
sudo fdisk -l
```

Do you remember if you installed or changed anything before this started happening?

---

### Post by firedancer on 2007-05-23
lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:02.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

---

### Post by firedancer on 2007-05-23
fdisk -l

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7872     2015216    e  W95 FAT16 (LBA)



well, after i installed it , i was trying to get some things working, maybe tweaked little bit.
and suddenly after a few times at boot it would start. then it stopped, but soon after started again
i have tried getting ubuntu studio an stuff and had problems but that was after this.
i also installed beryl but removed it after slowing down the system a bit, 
well i heard (read) there's a problem with ati video cards , and if i'm not mistaking (check lspci) mine is is an ati videocard
i followed the thread with codes how to make the changes but i wanna be sure not to mess things up more , i have to work and have only this pc, 
thx for reaching out:KS  

i'm working right now, can't afford a broken pc now

---

### Post by firedancer on 2007-05-23
why does it say sdc

my third (internal) hdd is 'frozen', i used it the least, should i take it out didn't do it yet

---

### Post by Terl on 2007-05-23
How many drives do you have?  I don't even see a linux portion, I only see one drive (sdc).  What do you have installed on the pc?  Is it ubuntu only?  I don't see it on your fdisk....

Yes, I would take out drives that are dead.  I googled a little and found that a dead drive can cause looping in the start-up.

---

### Post by firedancer on 2007-05-23
ok, i will try get it out 

but my fdisk seems strange 

because it only shows the drve which i did not use (can't)

i only have ubuntu on sda now with a swap partition
sdb wasn't able to write or safe stuff on it , tried all sorts of things,  but i'm sure now there  is a better way after reading some threads. 

and previously fdisk showed those two hdd only and now the opposite , strange

I had a double boot xp-ubu, but now it's complete ubu after malwareadwarespyware problems on xp
used dban and did a reinstall

after first install and an few logins i think it started this long proces before booting up

so maybe i messed with something, 
first i'll try getting out the hdd
but i'v to finish some schoolreports first, really scared not to mess up more , aaarrggh #-o

---

### Post by firedancer on 2007-05-23
well i noticed now after years, that i have two physical drives , my had help 'customizing' this ,
i thought i had three internal hdd. with other words sdc is a partition which i was'nt able to reformat when doing the ubuntu install. 

i believe that my second hdd is not good, my bios says you have two and the third is broken have to replace it. 

so maybe part of it is broken !
i think i going to get it out anyway, to get that out of the way
Dban did not work on it either sdb , so i quess something is wrong with it. 

now my fdisk -l is    

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

u c what i mean and now i'm logged in as an administrator
so it was showing me the bad partition on my second hdd

i'll try remove the hdd later or tomorrow, need some help with it , added pci cards before but that's about it , so i'll go to a friend instead

---

### Post by Terl on 2007-05-23
Is it starting better with the bad drive out?

Yeah, drives do break.  I had one do that about 6 months ago.  I also had a one gig bar of ram go out on me (that made me sadder than the disk).  

I agree with you about being careful.  I would make copies of the schoolwork and burn it to cd just in case.  It is always a good idea to back up regularly, especially with the important things.

---

### Post by firedancer on 2007-05-23
l'll le6t u know after i take it out what the conditions are 


ok 

thnx , for the (moral) support


:D

---

### Post by firedancer on 2007-05-25
no bug , just broken hdd




ubuntu rocks


:KS

---

