---
title: "gnomebaker problem"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by gustavocm on 2007-06-09
hi! 
i am trying to burn a music CD and i'm getting this error:

```

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... giving up.
scsidev: 'ATA:/dev/hdc'
TOC Type: 0 = CD-DA
devname: 'ATA:/dev/hdc'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```

please someone help me...
what can i do?

---

### Post by gustavocm on 2007-06-09
whem i do **wodim --devices**

```

Beginning native device scan. This may take a while if devices are busy...
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdc exclusively (Device or resource busy)... giving up.
wodim: Overview of accessible drives (0 found) :
----------------------------------------------------------------------
----------------------------------------------------------------------

```

and **wodim -scanbus**

```

wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```

---

