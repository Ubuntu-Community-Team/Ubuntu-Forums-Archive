---
title: "Folder Share Permissions"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by ClareJonsson on 2006-02-27
Noob here just need a little help.

I have shared a folder using samba on Ubuntu, I can connect to it from windows, but cannot create or edit anything as it's owned by root. How do I change this?

Clare.

---

### Post by Sutekh on 2006-02-27
You will need to edit the entry for this share in your /etc/fstab.  Can you post the output of this command from a terminal window?```
cat /etc/fstab
```

What filesystem is the share folder?  NTFS or FAT?  

At this stage I would assume that the **umask** needs to be set for the share folder.  This **umask** flag sets the permissions for the share folder, allowing you to read, write (provided the folder is not NTFS) and execute files.

---

### Post by ClareJonsson on 2006-02-27
Hia,

I have just found out that I can take ownership of the folder with chown.

Thanks for the nippy reply though :) .

Clare.

---

