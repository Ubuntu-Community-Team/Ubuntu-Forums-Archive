---
title: "SMB Access to Vista Special Directories"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by chudman on 2008-03-13
I've got my smb mounting setup according to the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite) and *everything* works fine.  The problem I'm having is that 2 directories in this smb share are not allowing me to write or modify files.  In fact, they show up with a little lock symbol in Nautilus and when I execute an `ls -la /mnt/SHARE` it shows the two folders permissions as dr-xr-xr-x.  

Please note that these two folders are my Music and Pictures folders in Vista.  In Vista I went to the Start menu and changed the Pictures and Music buttons to point to the location of those files on my shared partition.  In other words, Vista sees these folders as the system-wide Pictures and Music folders.  Instead of C:\Users\Me\Pictures and C:\Users\Me\Music the paths are D:\Music and D:\Pics.  This causes the icons to change in Explorer and I'm guessing that Vista is doing something special to prevent Ubuntu from writing to them.  

Has anyone else run across this problem?  How can I overcome this?  I'm not particularly concerned with security on my small local network so any solution is welcomed.

Right now the relavent line in my /etc/fstab looks like 

```
//192.168.X.X/d$      /mnt/XXX      smbfs credentials=/root/.smdpassword,dmask=777,fmask=777,uid=1000,gid=1000       0       0


```

---

### Post by njparton on 2008-03-13
Rather than .../d$ in fstab, try two entries, one for d:\Pics and one for d:\music instead (along with a new mount point for the 2nd one)?

---

