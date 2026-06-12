---
title: "UAF Mirror"
date: 2008-08-21
forum: Alaska Team - US
---

### Post by FakeOutdoorsman on 2008-08-21
Anyone know why the Ubuntu repo mirror at ubuntu.cs.uaf.edu vanished?  I was getting some good speeds from it.

---

### Post by os2mac on 2008-08-22
I just altered my settings to it and it's working just fine


[http://ubuntu.cs.uaf.edu/ubuntu](http://ubuntu.cs.uaf.edu/ubuntu)

---

### Post by FakeOutdoorsman on 2008-08-22
Thanks.  It seems to have re-appeared now.

---

### Post by FakeOutdoorsman on 2008-12-05
The UAF server seems to be having issues again.  This time with aptitude update:
```
99% [7 Packages bzip2 0] [Connecting to ubuntu.cs.uaf.edu
(137.229.25.178)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ubuntu.cs.uaf.edu intrepid/main Packages

  Sub-process bzip2 returned an error code (2)
```
Using System -> Administration -> Software Sources:
```
GPG error: http://ubuntu.cs.uaf.edu intrepid Release: The following
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic
Signing Key <ftpmaster@ubuntu.com>Failed to fetch
http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/main/binary-i386/Packages.bz2
 Sub-process bzip2 returned an error code (2)
Failed to fetch
http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.bz2
 Sub-process bzip2 returned an error code (2)
Failed to fetch
http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz
 404 Not Found
Failed to fetch
http://ubuntu.cs.uaf.edu/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz
 404 Not Found
```
This occurs on two separate machines.  Is anyone else having problems?

---

### Post by grimdestripador on 2009-10-16
I spoke with tech support, and this is a known issue. It appears the RAID has failed, and it is having trouble updating some files.
This is a low priority, and has been for almost a year now.

---

### Post by FakeOutdoorsman on 2009-10-16
> **grimdestripador said:**
> I spoke with tech support, and this is a known issue. It appears the RAID has failed, and it is having trouble updating some files.
This is a low priority, and has been for almost a year now.

I was about to ask for this mirror to be removed due to it not working for almost a year and because the mirror maintainer never responded to my questions.

---

### Post by shadghost on 2010-10-21
sory for the late rely, but i know the person who ran it, and it had multiple hard drive fails, one failed, then about 2-3 weeks later a second one faield after he replaced the first, and then he was hit with hard times, so the server went down, for UAF people there is still [http://mirrors.arsc.edu/ubuntu/](http://mirrors.arsc.edu/ubuntu/)  (non-offisal)

---

