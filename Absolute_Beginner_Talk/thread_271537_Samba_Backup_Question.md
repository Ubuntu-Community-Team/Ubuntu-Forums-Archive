---
title: "Samba Backup Question"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by DarkKoopa on 2006-10-04
Hi all,

I have mounted a new drive at /home/backup_drive

I want to have my windows machines on the network backup document files to this drive during the night.  This means that I don't want the windows machines to have to authenticate.

Is this what I'm after?
[http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29)

Does this mean I don't have to create a new user in the user/group area?

(My ADSL home modem died, and I want to research it out before I go home and am internet-less ;) )

Thank you.

---

### Post by DarkKoopa on 2006-10-05
For the record, it works fine.

Only thing I would add to that wiki is to make sure you make a backup copy of the config file you are editing

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

All my Windows PCs backup fine :D

---

