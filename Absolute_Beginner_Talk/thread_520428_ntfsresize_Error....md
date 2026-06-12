---
title: "ntfsresize Error..."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-08
hi guys...

what do i do here?

You might resize at 211945525248 bytes or 211946 MB (freeing 88121 MB).
Please make a test run using both the -n and -s options before real resizing!
root@Darkstar:/home/shane# ntfsresize --no-action -s 211946M /dev/sdb1
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size    : 211945992704 bytes (211946 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 211946 MB (70.6%)
Collecting resizing constraints ...
Needed relocations : 13987287 (57292 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
[COLOR="Red"]ERROR: Extended record needed (1888 > 1024), not yet supported![/COLOR]
Please try to free less space.

thanks..

---

### Post by az on 2007-08-08
> **Hopeless said:**
> hi guys...

what do i do here?

You might resize at 211945525248 bytes or 211946 MB (freeing 88121 MB).
Please make a test run using both the -n and -s options before real resizing!
root@Darkstar:/home/shane# ntfsresize --no-action -s 211946M /dev/sdb1
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 300066406912 bytes (300067 MB)
Current device size: 300066407424 bytes (300067 MB)
New volume size    : 211945992704 bytes (211946 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 211946 MB (70.6%)
Collecting resizing constraints ...
Needed relocations : 13987287 (57292 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
[COLOR="Red"]ERROR: Extended record needed (1888 > 1024), not yet supported![/COLOR]
Please try to free less space.

thanks..
Try:

ntfsresize --no-action -s 211945M /dev/sdb1

You may have to keep going down.  I think ntfsresize is safe, but obtuse.  Instead of figuring out that it has to do something differently, it just quits.

---

### Post by Hopeless on 2007-08-08
thanks....is this the easiest way to do this? do you have an easier way?

---

