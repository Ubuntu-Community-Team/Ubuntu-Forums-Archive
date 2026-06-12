---
title: "Unable to create new backup folder.  Access Denied."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by mcfly1204 on 2007-09-19
I have an old Compaq server with 6.06 on one SCSI drive.  I created a raid 5 array and mounted it to /media.  I am attempting to access this array from a Win2k server running Veritas Backup Exec 9.1 in order to do some D2D backups.  However, while on the Win2k box, I cannot access the backup folder on the Ubuntu server.  When I try to access the backup folder, I am prompted with an error stating that access is denied.  I tried to change the privileges on the folder, chmod 0777 /media/raid5/backups, but I receive the same error.  

On a sidenote, I attempted to add the Ubuntu server to the Windows AD, but I cannot log on with Windows usernames.  Any thoughts on any of this would be greatly appreciated.  Config files available upon request.

---

### Post by cmnorton on 2007-09-19
How does the Win2k server, through SAMBA, or a Veritas Agent running on your Ubuntu server? 

If it's SAMBA, you'll need to modify your SAMBA config so that the user -- on the Win2k server -- who mounts this drive for backing up has the correct permissions, and the directory will also have to have ownership and/or permissions that would let the local user have the same access.

If this isn't it, what did I miss?

---

### Post by mcfly1204 on 2007-09-19
The Veritas Agent is not involved here given I am not backing up the Ubuntu Server, I am backing up to it.  I thought that had I been able to get the Ubuntu Server on the AD, then the permissions would be easier to deal with.  For whatever reasons, I cannot seem to figure out why I cannot log on with AD usernames.  I have another system running 6.06, and I can logon to it with AD usernames just fine.  I have compared the krb5.conf and smb.conf files numerous times, but no dice.

---

### Post by mattskr on 2007-09-19
Remember that Samba usernames and passwords can be different than local ones. 

use 'smbpasswd' to set a Samba password for a user.

---

