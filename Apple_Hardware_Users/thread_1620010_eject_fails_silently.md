---
title: "eject fails silently"
date: 2010-11-12
forum: Apple Hardware Users
---

### Post by naufraghi on 2010-11-12
```
[19:42] matteo@andromeda:~$ sudo dmidecode -s system-product-name
MacBook6,1
```
```

[19:42] matteo@andromeda:~$ uname -a
Linux andromeda 2.6.35-23-generic #37-Ubuntu SMP Fri Nov 5 19:16:29 UTC 2010 x86_64 GNU/Linux
```
```
[19:42] matteo@andromeda:~$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is not mounted
eject: `/dev/sr0' is not a mount point
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/sr0' using SCSI commands
eject: SCSI eject succeeded
```

but... the drive is still inside. The CD is ok, is a working Ubuntu install.

Any idea?

Thanks!
Matteo Bertini

---

