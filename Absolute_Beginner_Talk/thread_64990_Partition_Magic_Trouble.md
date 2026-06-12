---
title: "Partition Magic Trouble"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by olymoore on 2005-09-12
I am trying to setup a  partition with Partition Magic 8.0 so i can run Kubuntu 5.10 but when i select to create a new partition and choose the size label and type options (FAT, FAT32 etc) it comes up with - 

Error#2103
Partition of specified size could not be created

I have tryed looking in the Partiotion Magic 8.0 error messages and sotutions page but my problem number isnt there.  Can anyone see what im doing wrong.  Thanks for any help  Oly

Edit - I think it might have somthing to do with running ScanDisk or CHKDSK not to sure though.

---

### Post by Juergen on 2005-09-12
The (K)Ubuntu setup can create its own partitions, and usually this results in less problems than using a 3rd party tool.
You just need free space on your disk.

Or are you trying to resize an existing Windows partition to get this free space?
In this case you might have to defrag in Windows first, and hope that no files are left at the end of the partition.
Sometimes running defrag more than once helps...

---

### Post by poofyhairguy on 2005-09-12
[QUOTE=olymoore]I am trying to setup a  partition with Partition Magic 8.0 so i can run Kubuntu 5.10 but when i select to create a new partition and choose the size label and type options (FAT, FAT32 etc) it comes up with - 

Error#2103
Partition of specified size could not be created

I have tryed looking in the Partiotion Magic 8.0 error messages and sotutions page but my problem number isnt there.  Can anyone see what im doing wrong.  Thanks for any help  Oly

Edit - I think it might have somthing to do with running ScanDisk or CHKDSK not to sure though.[/QUOTE]

You must defrag the disk before you can do that.

---

### Post by America's Reject on 2005-09-12
Just resize and exit, so u get unacumulated space

---

