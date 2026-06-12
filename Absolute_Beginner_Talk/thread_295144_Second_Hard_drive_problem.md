---
title: "Second Hard drive problem"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Newbi'fied on 2006-11-07
I installed ubuntu yesterday on my first harddrive. I have two 120 gigabyte harddrives and one is chock full of music and documents. I mount it from my root account into the folder mystuff. I give permissions to my other account to be able to access it. When I go to my second account to access the mounted hard drive it still says I don't have permissions, and then when I go back to edit the folder from root account, it says the folder is read only and I cannot change anything because it is read-only. It is formatted in NTFS.
I was also wondering how to set up my second account so that the hard drive was mounted every time I booted into that account.

---

### Post by ReaderRat on 2006-11-07
NTFS **is** read-only from Ubuntu. You cannot write to it. To share the drive, it must be FAT32 or ext2.

---

### Post by Newbi'fied on 2006-11-07
does this mean i have to reformat it?

---

### Post by ReaderRat on 2006-11-07
EDIT: sorry, I posted to the wrong thread....ReaderRat
RE-EDIT: Someone with more knowledge will have to help you with this.

---

### Post by Newbi'fied on 2006-11-07
Ok. So in order for this to happen...all my documents and music and such will be destroyed in the process?

---

### Post by smoker on 2006-11-07
try this link for info:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

remember to back up data you think essential

hope this helps

---

### Post by bodhi.zazen on 2006-11-07
Fro rw access to NTFS try [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009)

However, RW to NTFS can destroy your data. Better to migrate your data to a FAT or ext3 partition.

---

