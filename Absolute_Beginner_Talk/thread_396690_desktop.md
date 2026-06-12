---
title: "desktop"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-29
i have messed up with the permissions and then for now i can't write or save any files

to my desktop , i showed ls- l and i got that 

muhammad@muhammad-desktop:~$ ls -l
total 39816
drwx------ 2 muhammad muhammad      4096 2007-03-19 20:16 amsn_received
-rw------- 1 muhammad muhammad 133955584 2007-03-29 05:22 core.4501
drwxr-xr-x 3 muhammad muhammad      4096 2007-03-22 00:01 Deathnote 22
d--------x 3 root     root          4096 2007-03-30 01:20 Desktop
-rw-r--r-- 1 root     root          1109 2007-03-29 23:19 dsniff.services
lrwxrwxrwx 1 muhammad muhammad        26 2007-03-16 17:46 Examples -> /usr/share/example-content
-rw------- 1 muhammad muhammad      4284 2007-03-17 18:04 nano.save


so i need to be able to write to my desktop i need to edit that permissions and make it available for the normal user

---

### Post by solar george on 2007-03-29
Try 
```
sudo chown muhammad:muhammad ~/Desktop
```

Then use the file manager to enable writing.

---

### Post by ceezax on 2007-03-29
i did

and for now i have this output

muhammad@muhammad-desktop:~$ ls -l
total 39816
drwx------ 2 muhammad muhammad      4096 2007-03-19 20:16 amsn_received
-rw------- 1 muhammad muhammad 133955584 2007-03-29 05:22 core.4501
drwxr-xr-x 3 muhammad muhammad      4096 2007-03-22 00:01 Deathnote 22
d--------x 3 muhammad muhammad      4096 2007-03-30 01:20 Desktop
-rw-r--r-- 1 root     root          1109 2007-03-29 23:19 dsniff.services
lrwxrwxrwx 1 muhammad muhammad        26 2007-03-16 17:46 Examples -> /usr/share/example-content
-rw------- 1 muhammad muhammad      4284 2007-03-17 18:04 nano.save


but i am still not able to write to the desktop ??????????????????????

---

### Post by solar george on 2007-03-29
Open the filemanager to your home directory.

Right click on Desktop, and select properties.

Under the permissions tab make sure that you are listed as able to "create and delete files" if not use the drop down menu to select it.

---

