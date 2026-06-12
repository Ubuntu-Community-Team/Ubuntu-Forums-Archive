---
title: "simple commands"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by phoenix24x on 2007-10-05
so i am attempting to mount a windows server....via the forums [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
*(n00btacular questions post-script)*


this leads to some fun beginner stuff. as a regular user i need to create a samba authentication file
```
sudo vim .smbcredentials
```

i edit the file with the proper credentials,  then i change the ownership and permissions of the file so that only root can access it 
```
sudo chown root .smbcredentials
```
```
sudo chmod 600 .smbcredentials 
```

tutorial on the forums now tells me to backup my fstab file and edit it to add this to the bottom line:
**//$SERVER/$SHARE $MOUNTPOINT $FS_TYPE credentials=$SMB_CREDENTIALS,uid=$UID,gid=$GID**

this leads to a couple questions
1. after i created .smbcredentials as a regular user i typed```

ls
``` but saw nothing, but when i ```
ls -all
``` it shows seven fields of goodies (fill in the blank please)
     PERMISSIONS??? (what do the dashes mean:confused:)
     ID?    (whats this:confused:)
     USER (owner:confused:)
     USER (permission, i thought the first field was permissions!:confused:)
     ID?    (whats this:confused:)
     DATE&TIME 
     FILE

2. also some questions about the: 
**//$SERVER/$SHARE $MOUNTPOINT $FS_TYPE credentials=$SMB_CREDENTIALS,uid=$UID,gid=$GID**
      a. do the dollar signs actually have to be in there:confused:
      b. what is a mountpoint:confused:

thanks in advance
/cheers

---

### Post by derby007 on 2007-10-05
Try a little reading @:
 [http://tldp.org/guides.html#abs](http://tldp.org/guides.html#abs)

---

