---
title: "dpgk destroyed?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2007-07-21
ok so i search all around around and tried pratcily everything and i i thought "sudo apt-get -f install" and that didnt work what is going on?

> 
boys@boys-linux:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Bus errordependency tree... 0%
boys@boys-linux:~$ sudo apt-get -f install
Reading package lists... Done
Bus errordependency tree... 0%
boys@boys-linux:~$ 


---

### Post by FleetAdmiral74 on 2007-07-21
What are you trying to do exactly?

---

### Post by notjohn101 on 2007-07-21
im trying to get aptitude or apt- get to work again because as of right now.....i cant install anything

---

### Post by eldepeche on 2007-07-21
What are you trying to install? Do you get an error message when running "sudo apt-get install <oackage>"?

---

### Post by notjohn101 on 2007-07-21
yes i get an error message on EVRYTHING i try to install

---

### Post by meierfra on 2007-07-21
I googled for "bus  errordependency tree" and only found two useful links. But both those cases  had error messages in "dmesg". So I suggest looking at the output of 


```
dmesg 
```

and see whether it contains any error messages.

---

### Post by notjohn101 on 2007-07-21
here idk if this will help anyone with my problem

> ta 4096 in
[  534.041348]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  534.097692] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  534.097697] ata1.00: Host Protected Area detected.
[  534.097699]      current size : 20008703 sectors (10244 MB)
[  534.097700]      native  size : 20010816 sectors (10245 MB)
[  534.130088] ata1.00: SET of native returned 0, expected 20010816
[  534.137615] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  534.137620] ata1.00: Host Protected Area detected.
[  534.137622]      current size : 20008703 sectors (10244 MB)
[  534.137623]      native  size : 20010816 sectors (10245 MB)
[  534.152292] ata1.00: SET of native returned 0, expected 20010816
[  534.152296] ata1.00: configured for UDMA/66
[  534.317395] ata1.01: configured for UDMA/33
[  534.317406] ata1: EH complete
[  537.850006] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  537.850012] ata1.00: (BMDMA stat 0x64)
[  537.850020] ata1.00: cmd c8/00:08:17:49:fd/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  537.850022]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  537.857329] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  537.857335] ata1.00: Host Protected Area detected.
[  537.857336]      current size : 20008703 sectors (10244 MB)
[  537.857338]      native  size : 20010816 sectors (10245 MB)
[  537.872127] ata1.00: SET of native returned 0, expected 20010816
[  537.881369] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  537.881374] ata1.00: Host Protected Area detected.
[  537.881376]      current size : 20008703 sectors (10244 MB)
[  537.881377]      native  size : 20010816 sectors (10245 MB)
[  537.894335] ata1.00: SET of native returned 0, expected 20010816
[  537.894339] ata1.00: configured for UDMA/66
[  538.061098] ata1.01: configured for UDMA/33
[  538.061108] ata1: EH complete
[  541.592060] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  541.592065] ata1.00: (BMDMA stat 0x64)
[  541.592073] ata1.00: cmd c8/00:08:17:49:fd/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  541.592075]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  541.597914] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  541.597920] ata1.00: Host Protected Area detected.
[  541.597921]      current size : 20008703 sectors (10244 MB)
[  541.597923]      native  size : 20010816 sectors (10245 MB)
[  541.614175] ata1.00: SET of native returned 0, expected 20010816
[  541.621952] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  541.621958] ata1.00: Host Protected Area detected.
[  541.621959]      current size : 20008703 sectors (10244 MB)
[  541.621960]      native  size : 20010816 sectors (10245 MB)
[  541.636386] ata1.00: SET of native returned 0, expected 20010816
[  541.636391] ata1.00: configured for UDMA/66
[  541.797754] ata1.01: configured for UDMA/33
[  541.797767] ata1: EH complete
[  545.334104] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  545.334110] ata1.00: (BMDMA stat 0x64)
[  545.334117] ata1.00: cmd c8/00:08:17:49:fd/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  545.334119]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  545.342614] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  545.342620] ata1.00: Host Protected Area detected.
[  545.342621]      current size : 20008703 sectors (10244 MB)
[  545.342623]      native  size : 20010816 sectors (10245 MB)
[  545.356228] ata1.00: SET of native returned 0, expected 20010816
[  545.366592] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  545.366597] ata1.00: Host Protected Area detected.
[  545.366599]      current size : 20008703 sectors (10244 MB)
[  545.366600]      native  size : 20010816 sectors (10245 MB)
[  545.378429] ata1.00: SET of native returned 0, expected 20010816
[  545.378433] ata1.00: configured for UDMA/66
[  545.542383] ata1.01: configured for UDMA/33
[  545.542394] ata1: EH complete
[  549.076146] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  549.076153] ata1.00: (BMDMA stat 0x64)
[  549.076161] ata1.00: cmd c8/00:08:17:49:fd/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  549.076163]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  549.082715] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  549.082720] ata1.00: Host Protected Area detected.
[  549.082722]      current size : 20008703 sectors (10244 MB)
[  549.082723]      native  size : 20010816 sectors (10245 MB)
[  549.098265] ata1.00: SET of native returned 0, expected 20010816
[  549.106709] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  549.106715] ata1.00: Host Protected Area detected.
[  549.106716]      current size : 20008703 sectors (10244 MB)
[  549.106718]      native  size : 20010816 sectors (10245 MB)
[  549.120476] ata1.00: SET of native returned 0, expected 20010816
[  549.120480] ata1.00: configured for UDMA/66
[  549.286481] ata1.01: configured for UDMA/33
[  549.286491] ata1: EH complete
[  552.829295] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  552.829301] ata1.00: (BMDMA stat 0x64)
[  552.829308] ata1.00: cmd c8/00:08:17:49:fd/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
[  552.829310]          res 51/40:00:18:49:fd/00:00:00:00:00/e0 Emask 0x9 (media error)
[  552.838198] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  552.838203] ata1.00: Host Protected Area detected.
[  552.838205]      current size : 20008703 sectors (10244 MB)
[  552.838206]      native  size : 20010816 sectors (10245 MB)
[  552.851416] ata1.00: SET of native returned 0, expected 20010816
[  552.862245] ata1.00: ata_hpa_resize 1: sectors = 20008703, hpa_sectors = 20010816
[  552.862250] ata1.00: Host Protected Area detected.
[  552.862251]      current size : 20008703 sectors (10244 MB)
[  552.862253]      native  size : 20010816 sectors (10245 MB)
[  552.873627] ata1.00: SET of native returned 0, expected 20010816
[  552.873631] ata1.00: configured for UDMA/66
[  553.037991] ata1.01: configured for UDMA/33
[  553.038004] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  553.038006] sda: Current [descriptor]: sense key: Medium Error
[  553.038009]     Additional sense: Unrecovered read error - auto reallocate failed
[  553.038015] Descriptor sense data with sense descriptors (in hex):
[  553.038017]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  553.038026]         00 fd 49 18 
[  553.038030] end_request: I/O error, dev sda, sector 16599320
[  553.038043] ata1: EH complete
[  553.039273] SCSI device sda: 20008703 512-byte hdwr sectors (10244 MB)
[  553.039521] sda: Write Protect is off
[  553.039524] sda: Mode Sense: 00 3a 00 00
[  553.040030] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  553.040534] SCSI device sda: 20008703 512-byte hdwr sectors (10244 MB)
[  553.040808] sda: Write Protect is off
[  553.040811] sda: Mode Sense: 00 3a 00 00
[  553.043457] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1371.872145] NTFS driver 2.1.28 [Flags: R/O MODULE].
[ 1371.894394] NTFS volume version 3.1.
boys@boys-linux:~$ 


---

### Post by meierfra on 2007-07-21
> sda: Current [descriptor]: sense key: Medium Error
[ 553.038009] Additional sense: Unrecovered read error - auto reallocate failed

May be you have some kind of hard drive  problem, but I don't really know. I suggest  to start a new thread with "hard drive  problem" in the title to get some attention.

---

### Post by FleetAdmiral74 on 2007-07-22
Damn, this is out of my area of knowledge...which is really limited :)

Bump for ya though, hope someone can help. Reinstalling apt should not be hard...

---

### Post by notjohn101 on 2007-07-22
how do i reinstall apt....if dpkg is not working....is there some kind of other way to install something

---

### Post by notjohn101 on 2007-07-22
bump

---

### Post by notjohn101 on 2007-07-22
bump....someones gotta no soemthing about this

---

