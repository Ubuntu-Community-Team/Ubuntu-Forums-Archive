---
title: "Access harddrive"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by amontonarpapeles on 2008-03-16
Hello, after installing ubuntu (studio) with gnome on my computer with two harddrives, both originally unformatted, I am only able to access the one ubuntu is installed on. When running fdisk -l, I receive the following:

```

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a361a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24416   196121488+  83  Linux
/dev/sda2           24417       24792     3020220    5  Extended
/dev/sda5           24417       24792     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

I am assuming /dev/sdb is the unformatted drive, which I wish to access. How can I gain access to the drive? Do I need to format it?

Thanks.

---

### Post by TeoBigusGeekus on 2008-03-16
System->Administration->Partition Editor
Format your drive and you are done.

---

### Post by amontonarpapeles on 2008-03-16
I don't have that option on my administration menu. Could you give me the application name?

---

### Post by TeoBigusGeekus on 2008-03-16
I'm sorry, I thought it is preinstalled on Ubuntu.
Go to Synaptic and install gparted.

---

### Post by amontonarpapeles on 2008-03-16
It worked! Thank you.

---

