---
title: "howto mount and read what is on a harddrive"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by okkie on 2008-02-11
is there an easy way to mount master and or slave drives and to find out what is on them/what file system is used.what i read so far is very complicated.thanks

---

### Post by hyper_ch on 2008-02-11
(1) make a mountpoint

```

sudo mkdir /media/DRIVE_XXX

```
replace DRIVE_XXX with whatever you want to call it

(2) mount it:
```

sudo mount /dev/HDX /media/DRIVE_XXX

```

---

### Post by Ardrias on 2008-02-11
If you're unsure what your harddrives are called you can have a look through /var/log/messages to find out their names. What you're looking for is something like this:

```
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] Write Protect is off
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors (200050 MB)
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] Write Protect is off
Feb 11 14:21:14 albatross kernel: [    6.792000] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

The disk above would be located at /dev/sdb

---

### Post by hyper_ch on 2008-02-11
or issue:

 ```

sudo fdisk -l

```

that lists them all.

---

### Post by okkie on 2008-02-12
thanks gentlemen,my problem solved

---

