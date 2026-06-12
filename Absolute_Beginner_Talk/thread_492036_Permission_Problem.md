---
title: "Permission Problem"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Kreuzfeuer on 2007-07-04
I've go a second hard drive mounted at /media/disk-1, trouble is that it's owner is root and i can't change it[properties->permissions->owner gives an error message "sorry, couldn't change the owner], even when i log in as root. could someone help me please?

---

### Post by Computer-Slave on 2007-07-04
Can u post these Details?

1.Hard Disk Type: USB/ATA/SATA/SATA II
2.Hard Disk Partition Format: FAT16/FAT32/NTFS and etc.
3.Vendor: Maxtor/Seagate or etc.

---

### Post by Kreuzfeuer on 2007-07-04
1.Hard Disk Type: ATA
2.Hard Disk Partition Format: FAT32
3.Vendor: i think seagate, but i'm not quiet sure. would have to open the computer if it's really important

---

### Post by Nythain on 2007-07-04
sudo chown 1000:1000 /media/disk-1

---

### Post by Kreuzfeuer on 2007-07-04
message: "chown: changing ownership of `/media/disk-1': Operation not permitted"

---

### Post by dondad on 2007-07-04
> **Kreuzfeuer said:**
> message: "chown: changing ownership of `/media/disk-1': Operation not permitted"

did you use sudo?

---

### Post by Kreuzfeuer on 2007-07-04
i tried sudo and root-account.

i tried 

sudo chown -R user:root /media

which produced an error message for every file and folder in disk-1

---

### Post by Computer-Slave on 2007-07-05
> **Kreuzfeuer said:**
> 1.Hard Disk Type: ATA
2.Hard Disk Partition Format: FAT32
3.Vendor: i think seagate, but i'm not quiet sure. would have to open the computer if it's really important
What is the type of the Hard Disk Partition? Primary or extended if Primary than the permission can't be changed.

---

### Post by Nythain on 2007-07-05
hehe... didnt notice it was fat... think you are gonna have to edit ownerships in fstab

whats your fstab look like

---

### Post by Kreuzfeuer on 2007-07-05
okay, i figured out what to do.

first i unmounted both harddrives, then i created folders in media for both fat32 partitions(both primary fat32) and changed ownership to my useraccount. then i edited fstab manually. works great, but i have to type "sudo mount -a" after i finished booting. is there a way to run sudo mount -a automatically while booting?

---

### Post by 00arthuryu on 2007-07-05
you can always put that in the start up
system - prefrences - session
and put a new command :popcorn:

---

### Post by Computer-Slave on 2007-07-07
> **Kreuzfeuer said:**
> okay, i figured out what to do.

first i unmounted both harddrives, then i created folders in media for both fat32 partitions(both primary fat32) and changed ownership to my useraccount. then i edited fstab manually. works great, but i have to type "sudo mount -a" after i finished booting. is there a way to run sudo mount -a automatically while booting?
You could do that by making a desktop icon or panel icon or by editing /etc/fstab (not sure abt this). Plz visit my site mentioned in the signature and become a registered user. You might find anything useful. I hope i helped.

Thanks!

---

### Post by Computer-Slave on 2007-07-07
> **Computer-Slave said:**
> You could do that by making a desktop icon or panel icon or by editing /etc/fstab (not sure abt this). Plz visit my site mentioned in the signature and become a registered user. You might find anything useful. I hope i helped.

Thanks!
And to know how to create desktop and panel icons u can visit [http://computerzone.wetpaint.com/page/Creating+Launchers](http://computerzone.wetpaint.com/page/Creating+Launchers) and plz become a registered user.

Thanks!

---

