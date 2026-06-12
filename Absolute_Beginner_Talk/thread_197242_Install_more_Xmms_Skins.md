---
title: "Install more Xmms Skins?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-15
It says: Error while copying to "/usr/share/xmms/Skins"
            You do not have permissions to write to this folder. :confused:

---

### Post by tronica on 2006-06-15
try

> sudo mv <whatever> ~/.xmms/Skins 

---

### Post by Drakkor on 2006-06-15
drakkor@drakkor:~$ sudo mv <chaos_XMMS.zip> ~/.xmms/Skins
bash: chaos_XMMS.zip: No such file or directory
The file is on the desktop !  :confused:

---

### Post by tronica on 2006-06-15
ok, so 
cd /home/drakkor/Desktop

then

sudo mv chaos_XMMS.zip ~/.xmms/Skins

---

### Post by Drakkor on 2006-06-15
Thanks, tronica, worked like a charm !  Cheers   :D

---

