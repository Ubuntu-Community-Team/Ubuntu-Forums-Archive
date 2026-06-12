---
title: "remote access permissions"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-04-09
how can i enable full read/write access to a subfolder of a shared folder on Ubuntu 7.10, where the shared folder is mapped from a separate windows xp system?  the share was created with the Read-only option unchecked, and i am able to view the contents of the subfolders within the mapped folder but i cannot write to them unless i create a share directly to the folder i want to write to and then map this share in windows xp..  the account i am logged into Ubuntu with has ownership of the shared folder.  thanks.

---

### Post by njparton on 2008-04-10
I assume you're using samba?
 
Take a look at the following config file towards the bottom:
 
```
/etc/samba/smb.conf
```
 
you may have it set to read-only in there?
 
Restart samba after any changes:
 
```
 
sudo /etc/init.d/samba restart

```

---

