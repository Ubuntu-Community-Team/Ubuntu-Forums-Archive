---
title: "Dvd burning Edgy Server (NEC ND-5170)"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pcw on 2007-03-16
Hey all,

I have installed Ubuntu Edgy Server 6.10 through a DVD that I placed in my NEC ND-5170 DVD burner so the burner is recognized by Ubuntu allright.

But after I have installed cdrecord (sudo aptitude install cdrecord) and enter this command to scan for my DVD burner "sudo cdrecord -scanbus" I get this message:

```

pcw@ubuntu:~$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'HDT722525DLA380 ' 'V44O' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) 'ATA     ' 'SAMSUNG SP2504C ' 'VT10' Disk
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *
pcw@ubuntu:~$

```

There's a warning about unofficial version of libscg and it only finds my harddrives it seems like.

---

### Post by pcw on 2007-03-16
I read some about cdrecord on the forums and one post suggest to try this command "sudo cdrecord dev=/dev/hdc -scanbus"

And it seems that it now found my DVD burner. Does this mean that I can try burning a DVD now?

```

pcw@ubuntu:~$ sudo cdrecord dev=/dev/hdc -scanbus
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) 'Optiarc ' 'DVD RW AD-5170A ' '1.11' Removable CD-ROM
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *
pcw@ubuntu:~$

```

---

