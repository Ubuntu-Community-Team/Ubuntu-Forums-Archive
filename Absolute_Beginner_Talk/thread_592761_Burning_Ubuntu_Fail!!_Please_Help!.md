---
title: "Burning Ubuntu Fail!! Please Help!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-10-26
Every time I try burning the lasted Xubuntu it fails. Here is how it goes.

```

$ cdrecord dev=/dev/scd1 driveropts=burnfree -data xubuntu-7.10-alternate-i386.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identification : 'DVD_RW ND-3500AG'
Revision       : '2.16'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Speed set to 5645 KB/s
Starting to write CD/DVD at speed  32.0 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 32 20 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 2F 7A 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 12154 (not valid) 
resid: 32768
cmd finished after 23.462s timeout 40s
write track data: error after 26279936 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.004s timeout 480s
cmd finished after 0.004s timeout 480s
wodim: Cannot fixate disk.

```

Any help will be awesome.

---

### Post by Pumalite on 2007-10-26
Download a new iso. Do md5sum before burn. Burn at 4x. Use k3b in Linux or ImgBurn in Windows.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(make sure you burn as 'Image' and not 'data')

---

### Post by Niniel on 2007-10-26
ImgBurn did not improve things for me at all. I ended up using [[COLOR="Blue"]_CDBurnerXP_[/COLOR]]("http://cdburnerxp.se/") and burned at 16 x to CD/R. Still took several tries. Speed didn't seem to be that important - I had some success at 25 x, and I failed several times at 4x as well. Once you got a good ISO, you'll just have to keep trying.

---

### Post by Pumalite on 2007-10-26
ImgBurn is by the maker of the legendary DVD Decryter and is an excellent burner.
You go to Mode>ISO>Burn

---

### Post by mikewhatever on 2007-10-26
Not sure whether this is relevant, but use a good quality CDs, not some cheap junk. Redownloading the iso does not make sure there are no errors, you have to md5sum check.

---

### Post by jaybombalous on 2007-10-26
nvm, I read the original post wrong. u already have ubuntu, u want xubuntu? Try d/l'ing using torrent file and deluge.

---

### Post by ddrichardson on 2007-10-26
Does the error always occur here:```

write track data: error after 26279936 bytes
```

---

### Post by Pumalite on 2007-10-26
Taiyo Yuden
Verbatim

---

### Post by guysmiley25 on 2007-10-27
The iso file itself is fine. The md5sum works out.

I am already running Xubuntu but i want to burn off a copy of the latest version to install on my laptop.

I'm not at that machine at the moment but I think that the error is always happing around there.

I've tried xfburn and graveman. Got errors with both. I prefer the command line anyway.

Thanks everyone for the help so far.

---

