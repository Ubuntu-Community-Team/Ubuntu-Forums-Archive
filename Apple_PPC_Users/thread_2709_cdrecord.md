---
title: "cdrecord"
date: 2004-10-30
forum: Apple PPC Users
---

### Post by khc on 2004-10-30
cdrecord -scanbus
<snip>
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord -scanbus -dev=ATAPI
<snip>
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related libscg interface code is in pre alpha.
Warning: There may be fatal problems.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
.....

How to get cdrecord to detect the burner? I have a 867MHz Tibook

---

### Post by mpfleger on 2004-12-16
Hi.

I *just* ran into this very same problem.  <edit />

OK; so I just found out what's going on.  The 2.6.x kernels do not apparently need to have the scsi devices.  Try:
    cdrecord -dev=/dev/cdrom

whee!
-m

---

