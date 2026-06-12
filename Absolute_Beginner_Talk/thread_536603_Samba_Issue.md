---
title: "Samba Issue"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-27
I have two Ubuntu computers with the same samba username and password. I have shared files on both computers with both read and write access. I can access and modify these shared files for both computers though my Windows XP computer. However, when I try to access files between the two Ubuntu boxes, I get the following error:

You do not have the permissions necessary to view the contents

However, if I make the share read-only though the GUI, I can access the shares between the two Ubuntu boxes. But in read/write mode, I cannot even view the files. Please help. Thank you.

---

### Post by uclalinux on 2007-08-28
You might need to add a write list to your smb.conf file. 

```
[home]
read only = no
browesable = no

["username"]
path = /home/"username"
browseable  = yes
write list = "username"
read only = no
```

---

