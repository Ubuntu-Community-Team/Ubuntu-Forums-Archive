---
title: "[SOLVED] Change backup directory in BackupPC"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-07
Hi there,

I'm new to backuppc and just filled my root partition. I have a 500GB disk mounted in /home/backups - how do I tell backuppc to put all backups in that partition? Also, how do I delete the backups that were placed in / - none of them completed so there's no option in the web interface to remove them, however the / partition is full. 

Thanks.

---

### Post by dcstar on 2007-09-07
> **keymoo said:**
> Hi there,

I'm new to backuppc and just filled my root partition. I have a 500GB disk mounted in /home/backups - how do I tell backuppc to put all backups in that partition? Also, how do I delete the backups that were placed in / - none of them completed so there's no option in the web interface to remove them, however the / partition is full. 

Thanks.

On the assumption that you need root permissions to delete these backups, create a new Launcher with the following in the Command field:

```
gksudo nautilus
```

When you start this you will asked to enter your password to gain root access, so be very careful as you now can delete any system file and potentially damage your installation!

---

### Post by keymoo on 2007-09-07
Thanks David, but I don't know which files to delete without breaking backuppc. Could you guide me here? I don't have a GUI either as I'm using Ubuntu Server 7.04 - I do however have the File Manager in Webmin.

---

### Post by keymoo on 2007-09-09
I rebuilt the server - running great now.

---

