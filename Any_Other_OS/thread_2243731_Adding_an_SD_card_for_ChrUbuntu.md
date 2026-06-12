---
title: "Adding an SD card for ChrUbuntu"
date: 2014-09-10
forum: Any Other OS
---

### Post by Gabriel_Haywood on 2014-09-10
Hello. 
I've recently downloaded ChrUbuntu to on my Acer C720. Now that I've downloaded it, I want more space. If I put an SD card in there now, would it go to ChrUbuntu or Chrome OS? Thanks!

---

### Post by TheFu on 2014-09-10
Hummmmm. I'd think it would become available to whichever OS is booted at the time. Let me try on my C720 ... oh - I don't have chromeos anymore, so can't test that. Sorry.

The SDHC is external storage and would be treated like that by either OS.

So on my 14.04 install on the C720 - the SDHC storage was mounted to /media/{userid}/{UUID} - 

```
Model: Generic Power Saving USB (scsi)
Disk /dev/sdb: 3965MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  3965MB  3965MB  ntfs

```

Hope that helps on some level.

---

### Post by QIII on 2014-09-10
*Moved to **Other Operating Systems and Projects***

---

### Post by Gabriel_Haywood on 2014-09-12
Thanks, I'll try it when I buy an SD card. I probably should have posted this after I brought one.

---

