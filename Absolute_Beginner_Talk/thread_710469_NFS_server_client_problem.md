---
title: "NFS server client problem"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2008-02-28
I used to have a NFS server set up then i had to reformat for various reason and i set it back up but for some reason its not working correctly.  here is my exports file 

[B]/home/Uploads 192.168.1.0/24(rw,no_root_squash,async)
/home/Videos 192.168.1.0/24(ro,async)
/home/Pictures 192.168.1.0/24(ro,async)
/home/Documents 192.168.1.0/24(ro,async)
/home/Music 192.168.1.0/24(ro,async)[/B]

and when i run **sudo exportfs -a** i get this output

[B]exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/home/Uploads".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
[/B]

any ideas

---

### Post by Martje_001 on 2008-02-28
Add **subtree_check** to **(ro,async)**

---

### Post by poordamnedfool on 2008-02-28
That worked thanks a lot there is only one more problem on the uploads folder, from the client computer you cannot upload files to it.

---

### Post by Martje_001 on 2008-02-29
```
chown yourusername /upload/folder
```
does this work?

---

