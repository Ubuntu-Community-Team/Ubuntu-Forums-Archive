---
title: "Can't find second hard drive."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-10-17
Installing ubuntu serer on a couple dell servers.  Both servers have 2 SATA hard drives.  During install i could see both.  after the install if i fdisk /dev/sdb through sdz i cannot seem to find what the os thinks my drives are.  how can I tell what ubuntu thinks my /dev device is?

Thanks

Bill

---

### Post by meierfra on 2007-10-17
```
sudo fdisk -l
```

---

### Post by mlind on 2007-10-17
Output of *sudo fdisk -l * should show you all the drives and their partitions. Did you create RAID array(s) and/or LVM during the install ?

---

### Post by BillGod on 2007-10-17
I tried fdsik -l  It only shows sda with its partitions.  There are no partitions on the other drive.  This was a clean install on brand new hardware.  No raid setup.  just chose to install to the first hard drive.  The installer showed both 250gb drives at this point.  just dont know where its hiding.

---

### Post by mlind on 2007-10-17
does output of dmesg or lshw show you that kernel actually found 2 SATA drives during boot?

```

dmesg | less
sudo lshw | less

```

---

### Post by battyice on 2007-10-17
What does your /etc/fstab file look like?  Is the second disk listed?

When you installed the OS, did you format the drive and assign a mount point?

---

