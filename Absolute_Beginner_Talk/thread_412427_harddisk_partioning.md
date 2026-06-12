---
title: "harddisk partioning"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by hardipdhillon on 2007-04-18
[SIZE="5"]At the installation time i just format one scsi harddisk and left others as such,Now there are three scsi harddisk in my server,so i want to format other ones,how can i do this

---

### Post by Bachstelze on 2007-04-18
Either with fdisk/mkfs in the command line or GParted if you want a GUI.

---

### Post by hardipdhillon on 2007-04-18
how can i check the name of the scsi disk , it is not shown in fstab

---

### Post by Bachstelze on 2007-04-18
```
cat /proc/partitions
```

for example...

---

### Post by hardipdhillon on 2007-04-18
yes i checked it, it shows sda,sdb,sdc i want to format sdb & sdc ,i try fdisk sdb it gives the error "unable to open sdb" do i have to some thing before giving fdisk command

---

### Post by Bachstelze on 2007-04-18
Try with /dev/sdb

---

