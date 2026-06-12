---
title: "writing on vfat partition"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by pranab_cool on 2006-10-17
](*,) i am new to ubuntu or for that matter linux. 
i m not able to write onto my other partitions - 2 vfat and one ntfs. i heard that writing is not permitted onto ntfs partition in linux. how to do that in vfat. i m only able to read frm the partitions. 
plz suggest something. its imp for me as my ubuntu partition is not v large which makes it inevitable for me to use other partitions.

---

### Post by apjone on 2006-10-17
the vfat partions must have been mounted read only for users. If you use sudo to copy a file to the vfat partion does that work??

---

### Post by pranab_cool on 2006-10-17
i m really dumb to even know what sudo is!!! 
so plz if u can spare some time to help me solve my prob.

---

### Post by docshawnc on 2006-10-17
Since ubuntu (by default) doesn't have a super user account, you need a way to do super user stuff - this is accomplished through the use of the sudo command.

to try to copy a file to a vfat drive, open a terminal window and type:

sudo nautilus

it will ask for your pw and then bring up a window.  Use this window to try and copy/paste a file onto the vfat drive.  Of successful, you may want to change something in a file called /etc/fstab (where various permissions are assigned on boot)

---

