---
title: "Swap doesnt go on at startup"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-08-24
[SIZE="3"]Hi, whenever i start my computer, my swap doesnt go on..
I have to manually turn it on.

also, i seem to not be able to edit /ect/fstab
it's read only and says that i dont have permission to change it.


under users and groups im marked as an admin and root.

any help would be great! thanks.[/SIZE]

---

### Post by p_quarles on 2007-08-24
Open a terminal (alt-F1) and type the following:
```
free
```
Then, paste the output into a message here.

---

### Post by nitro_n2o on 2007-08-24
all right if you insist on editing the file.. start the terminal and type 
```
gksudo gedit /etc/fstab
```

---

### Post by p_quarles on 2007-08-24
> **nitro_n2o said:**
> all right if you insist on editing the file.. start the terminal and type 
```
gksudo gedit /etc/fstab
```
Right, but *don't *manually add the swap partition to /etc/fstab until we've seen the output from "free."

---

### Post by Trzone on 2007-08-24
[SIZE="3"]Im a step ahead of you, i went through the forums and found gksudo nautilus which i was then able to access a read-write form of the etc/fstab
and then i found out the UUID since i had reformated the partition
copy, paste, save.
it works now, i just can't access the file normally![/SIZE]


Just a reinstall did the trick, and i backed it up after i reinstalled everything, so now im able to just mess around with ubuntu! haha

---

