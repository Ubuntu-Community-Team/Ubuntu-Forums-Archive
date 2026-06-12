---
title: "[SOLVED] create mount point"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-27
i moved all of  my music to my home folder reformatted my secondary drive to primary ext3 it is
the 80 GB disk

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

how do i make it mount automatically???

---

### Post by Inxsible on 2007-08-27
if its an external use pmount. see my sig

if its an internal, paste your fstab, you probably only need to add "auto" as an option there.

---

### Post by yellowband on 2007-08-27
put a new line in your /etc/fstab file like this

```
 sudo gedit /etc/fstab 
```

the new line would be something like:

/dev/sdb1   /mount/new_drive    ext3     defaults    0     0


remember to make the folder /mount/new_drive first (this directory can be anywhere by the way)

---

### Post by Seti on 2007-08-27
Edit your fstab file to tell it to mount your filesystem automatically.

```
sudo gedit /etc/fstab
```
put 'defaults' under the <options> column for your desired mountpoint

good luck

---

### Post by DarinB on 2007-08-27
worked like a charm thanks i copied over my music and iam up and running
i used

/dev/sdb1 /mount/new_drive ext3 defaults 0 0

---

