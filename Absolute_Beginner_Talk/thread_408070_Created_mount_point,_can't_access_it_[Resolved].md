---
title: "Created mount point, can't access it [Resolved]"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by fsmpastafarian on 2007-04-12
I have a dual boot system, Ubuntu 6.10 and WinXP.  I have 2 500GB harddrives, and I have Windows and Ubuntu on sda.  Both operating systems seem to work ok.  

On the second harddrive, I intend to store data, so I have created an NTFS partition and an ext3 partition.  Windows recognizes the NTFS partion as D:, and works ok with it.  I tried to set up a mount point in the ext3 partition.  In File Browser, I can see my mount point, its /mnt/data.  When I try to drag and drop a file into it, I get an error "Error while copying to "/mnt/data".  You do not have permission to write to this folder"  

Here is my fstab:

# /dev/sda2
UUID=cc0edf10-5121-4d83-ac27-1e012dfd7f83 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1
UUID=38CC441DCC43D3B2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/sda3
UUID=c2c35daa-3b82-4bd7-a703-bfd681243d74 none            swap    sw              0       0

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


#/dev/sdb2 
UUID=994be388-cf6a-4e1d-9762-ca03846a348b /mnt/data ext3 users,uid=1000,auto 0 0


Thanks in advance for any help.

---

### Post by taurus on 2007-04-12
Try using chmod to change the ownership of /mnt/data from root to your login name.  Assuming your login name is **fsmpastafarian**, open a terminal and do

```
sudo chown -R **fsmpastafarian**:**fsmpastafarian** /mnt/data
ls -la /mnt
```

---

### Post by fsmpastafarian on 2007-04-13
Taurus,

Thanks, that worked.

FSM

---

