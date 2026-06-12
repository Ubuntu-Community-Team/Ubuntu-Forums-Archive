---
title: "boot problems /dev/hda1..fstab"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-29
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

ubuntu@ubuntu:~$ gksudo gedit /mnt/ubuntu/etc/fstab

(gedit:7631): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$


i dont know if i did this the right way but here is what happend
Edit/Delete Message

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 23944 192330148+ 83 Linux
/dev/hda2 23945 24321 3028252+ 5 Extended
/dev/hda5 23945 24321 3028221 82 Linux swap / Solaris

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 10011 80413326 83 Linux
ubuntu@ubuntu:~$



here is the out put
Edit/Delete Message

i am having some problems rebooting i have printed my efforts so far need help to solve this problem

at boot it goes to a forced boot and i end up with this 
/dev/hda1/:unexpected inconsistency
 run fsck manually
 ie .,without -a or -p options 
line in etc/fstab is bad
 i am running a live disk so i should be able to fix but i dont know what to do now ](*,)  ](*,)

---

### Post by lloyd_b on 2006-10-29
What you need to do:

```
**sudo fsck /dev/hda1**
```

This will check (and hopefully repair) the partition.  

Lloyd B.

---

### Post by wieman01 on 2006-10-29
Tried this?
> sudo mount /dev/hda1 /mnt/ubuntu
Not "-t ext3" option.

But frankly I think there is a problem with the file system. Not sure if you can fix it if "fsck" fails you. Have you given "fsck" a shot at all?

---

### Post by STREETURCHINE on 2006-10-29
> **lloyd_b said:**
> What you need to do:

```
**sudo fsck /dev/hda1**
```

This will check (and hopefully repair) the partition.  

Lloyd B.

thanks that solved my problem 
 thanks to all that helped:-D

---

