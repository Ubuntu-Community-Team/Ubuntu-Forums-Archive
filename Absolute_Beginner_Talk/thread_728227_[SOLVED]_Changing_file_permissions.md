---
title: "[SOLVED] Changing file permissions"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Riverbanks on 2008-03-18
I'm having problems with the file permissions on my second HD.  I recently reinstalled Ubuntu, but now all the files on my second HD are owned by a user called "bin", and I am unable to change the owner or the permissions.  I can access the files, but not write to them.  Is there any way to change the owner of the files?

---

### Post by taurus on 2008-03-18
How do you mount that second harddrive?  If it's not part of the system, you can change the ownership of that mount point from bin to your login name so you can write to it anytime you want.

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

### Post by PeterJS on 2008-03-18
Since you are not currently the owner of the files, you will need administrative privilages to change thier ownership.
```

sudo chown *new_username*:*new_groupname* -R /media/somedrive

```

---

### Post by Riverbanks on 2008-03-18
I mounted the HD by adding the following code to my fstab file:

/dev/hdb1	/media/hdb1	vfat	umask=0222,dmask=0000,uid=0002,gid=users,users  0 0

so I just need to find a way to change the owner of /media/hdb1, I guess

---

### Post by PeterJS on 2008-03-18
> **Riverbanks said:**
> I mounted the HD by adding the following code to my fstab file:

/dev/hdb1	/media/hdb1	vfat	umask=0222,dmask=0000,**uid=0002**,gid=users,users  0 0

so I just need to find a way to change the owner of /media/hdb1, I guess

There we go, if you change the uid the drive is mount with to the uid of your account you should be golden.

---

### Post by Riverbanks on 2008-03-18
Hmmmm.   I tried chown, but it just gave me a million error messages saying "operation not permitted".

---

### Post by PeterJS on 2008-03-18
> **Riverbanks said:**
> Hmmmm.   I tried chown, but it just gave me a million error messages saying "operation not permitted".

Yeah, sorry about that, I wrongly assumed you were using a native file system that supported permissions. It was a bad assumption.

---

### Post by Riverbanks on 2008-03-18
Yeah, that HD is formatted with FAT32, I guess that causes problems...

---

### Post by Riverbanks on 2008-03-18
Problem solved!

I just changed the uid in fstab like PeterJS suggested, and then had to manually unmount then remount the drive to get the change to take effect.
Thanks guys!

---

