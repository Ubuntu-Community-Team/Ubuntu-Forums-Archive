---
title: "Mounting an NTFS Share"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Lindsay Cole on 2006-02-17
How do I go about mounting an NTFS Share across the network?

I have security set to share. But it just won't let me do it...

thanks!

---

### Post by patrick295767 on 2006-02-17
```
mount -t smbfs //ipadress/share /mnt/mountpoint -o username=yourusername,password=yourpassword
```
  
Plz also in windows, make sure when u share ur folder
u have to add the user + give rights in **BOTH ** SECURITY and SHARINGacesss Tabs 

Greetz

Pat

---

