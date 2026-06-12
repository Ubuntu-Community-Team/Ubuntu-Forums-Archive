---
title: "mdadm - how to list disks labelled as &quot;removed&quot;"
date: 2012-02-15
forum: Apple Hardware Users
---

### Post by allebone on 2012-02-15
On G5 12.04

When using mdadm --detail 
I can view the details of all the disks online and their mount points eg:

/dev/sdc1 etc

But if a disk is taken offline it appears as 
"removed" and doesnt show what the mound point was.

In the GUI disk manager - it is still able to show what the disk was that was removed.

How can one find this information via the command line? I cant seem to work out how to ascertain the name(mount point) of the removed disk via the cli.

Pete

---

### Post by allebone on 2012-02-22
> **allebone said:**
> On G5 12.04

When using mdadm --detail 
I can view the details of all the disks online and their mount points eg:

/dev/sdc1 etc

But if a disk is taken offline it appears as 
"removed" and doesnt show what the mound point was.

In the GUI disk manager - it is still able to show what the disk was that was removed.

How can one find this information via the command line? I cant seem to work out how to ascertain the name(mount point) of the removed disk via the cli.

Pete


I made some headway, you can view all the disks by doing 

sudo cat /proc/partitions

and "guess" which it is via the size of the partitions (they will be similar).

Pete

---

