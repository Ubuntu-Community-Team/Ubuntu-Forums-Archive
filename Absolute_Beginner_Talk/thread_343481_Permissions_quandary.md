---
title: "Permissions quandary"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by kook44 on 2007-01-21
Hi-
I'm having some confusion about permissions settings.
I have a folder /data, which is owner/group: root/root, and permissions 755.  I created a subdirectory /data/subversion - owner/group: root/svnusers, permissions 775.  I've added myself to the group svnusers, but I get permission denied when I try to mkdir inside of /data/subversion.

Am I missing something here?

Thanks!

---

### Post by taurus on 2007-01-21
755 on /data means only root can create directories under it.  Group can only read and execute.  What you want is to change the permission of /data to 775.

```
sudo chgrp -R svnusers /data
sudo chmod -R 775 /data
```

---

