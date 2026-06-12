---
title: "hdb not showing"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-16
I finally took the plunge and went totally ubuntu last night(Bye Bye Windoze). I installed over XP pro on hda last night. I put in the live CD and formatted hdb (120GB) to ext3 and sda also. sdb is 120 gb NTFS with lots of data on it that I want to put on hdb and then reformat to ext3. sda appears on my desktop as "usb Disk" and sdb appears as "Local Disk" but hdb is nowhere to be found. ](*,) What did I miss when I reformatted? Thank you in advance for your help, everyone here is so patient and helpful.

---

### Post by taurus on 2007-01-16
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kliljedahl on 2007-01-16
I got this: 
kliljedahl@kliljedahl-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631   83  Linux

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14946   120053713+   7  HPFS/NTFS
kliljedahl@kliljedahl-desktop:~$

---

### Post by taurus on 2007-01-16
Edit your /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by kliljedahl on 2007-01-16
Did step #1 and got this: 
(gedit:7707): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:7707): WARNING **: Hit unhandled case 19 (Not a directory) in gedit_unrecoverable_loading_error_message_area_new.

---

### Post by kliljedahl on 2007-01-16
OK, I rebooted and it's showing. I tried to copy and past from sdb to hdb and was told I don't have permission to write to to hdb.

---

### Post by taurus on 2007-01-16
```
sudo chown -R **username**:**username** /media/hdb1
```
Replace the **username** with the _actual_ username that you log in...

---

### Post by kliljedahl on 2007-01-16
Thank you so very much. i'm saving all of these so I shouldn't have the same problem with sdb once everything transfers. I have so much to learn, but I intend to learn it. Your help and patience is greatly appreciated.

---

### Post by taurus on 2007-01-16
Glad to hear that you can write to /media/hdb1 as a regular user, without using sudo.

---

### Post by kliljedahl on 2007-01-16
I just opened both and dragged from sdb to hdb, didn't even have to copy and paste. I'll reformat sdb in the morning (hopefully everything will be transferred by then). Once again, thanks for your help and patience.

---

