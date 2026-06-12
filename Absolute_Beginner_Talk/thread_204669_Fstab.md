---
title: "Fstab"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-06-27
i added a dvd writer to my hardware.
is there a way to get the fstab configured again in stead of manually editing?

tv

---

### Post by Ctrl+Alt+Del on 2006-06-27
not to my knowledge, but editing it is pretty trivial
just type sudo nano -w /etc/fstab and add a line like
```
/dev/hdd                /mnt/dvdr       iso9660,udf     noauto,ro,user          0 0
```
depending on your setup the /dev part could be different
secondary master = hdb
primary slave = hdc
secondary slave = hdd
if it's sata/scsi hardware it will be sd instead of hd
now all you have to do is create the dir you specified in /mnt

---

### Post by drtvasudevan on 2006-06-27
ok thanks
tv

---

