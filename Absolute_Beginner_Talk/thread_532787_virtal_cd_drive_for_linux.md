---
title: "virtal cd drive for linux"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2007-08-23
I need a virtual cd drive that will mount my iso or bin cd images 
how do i do it

---

### Post by schorsch on 2007-08-23
The following command should work for iso-files:
```
 sudo mount -t iso9660 /<path_to_iso_file> /<desired_mount_pount>
```
Just replace "<path_to_iso_file>" and "<desired_mount_point>" with the appropriate values. I am not sure if this will work for bin-files, too.

---

