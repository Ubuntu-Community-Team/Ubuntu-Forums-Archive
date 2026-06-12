---
title: "Mounting a partition"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-03-11
Im having trouble mounting a partition correctly.  I used gparted to partition a drive i have with ext2.   Its listed as dev/hdb2 and i have used the mkdir command to make the directory /media/Virtual(going to be holding vmware images only) to mount it in.  How do i mount this to have full read write priveleges to the drive.  I got it mounted last night, but it will not allow reading and writing.

---

### Post by meindian523 on 2008-03-11
Add it to the /etc/fstab.

---

### Post by meindian523 on 2008-03-11
```
/dev/hdb2 /media/virtual ext2 defaults,user,auto 0 2
```

would be the appropriate entry.

---

### Post by dstew on 2008-03-11
The simple command would be```
sudo mount /dev/hdb2 /media/Virtual
```If you get an error message, post it. If you want it to mount at boot-up every time, then you can add a line to your /etc/fstab file.

---

### Post by sisco311 on 2008-03-11
after you mounted, chown the partition
```
sudo chown -R your_username:your_username /media/Virtual
```

---

### Post by Mauler5858 on 2008-03-11
Sweet thanks!!
```
sudo mount /dev/hdb2 /media/Virtual
``` 
&
```
sudo chown -R your_username:your_username /media/Virtual
```

Those worked like a charm.

---

