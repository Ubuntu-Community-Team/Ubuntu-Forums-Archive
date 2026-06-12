---
title: "folder permissions"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by redmonster13 on 2007-08-18
I have a secondary hard drive for storage buy I have no idea how to give myself write permissions for it, could someone please throw me a bone here ?

---

### Post by taurus on 2007-08-18
Is it ntfs filesystem?  If yes, then you need to read this link to install ntfs-3g and use it to mount that drive before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by redmonster13 on 2007-08-18
I have formated the storage drive as ext3 and I right clicked and mounted it, but I still cant write to it. Any sugestions?

---

### Post by taurus on 2007-08-18
What is the mount point of that harddrive?  You just need to change the ownership of that mount point from root to your login name and you can write to it anytime you want.

```
id
```
_Assuming_ you mount it to /media/storage and your login name is **redmonster**, do

```
sudo chown -R **redmonster**:**redmonster** /media/storage
ls -la /media
```

---

### Post by redmonster13 on 2007-08-18
worked like a charm, thank you very much

Any advice on formating the last partition back to ntfs?

I split that drive in half and formated one half as ext3.

---

### Post by taurus on 2007-08-18
You can use gparted (System -> Administration) to format the second partition to ntfs filesystem if you wish.  Then, you need to use ntfs-3g to mount it so you can write to it as well.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by drworm01 on 2007-08-18
Thanks for posting the help. I was having the same problem and now I've got full permissions. Good deal.
I have a follow-up question though, how do you make the second hard drive auto-mount at startup?
Thanks a lot.

---

### Post by taurus on 2007-08-18
> **drworm01 said:**
> Thanks for posting the help. I was having the same problem and now I've got full permissions. Good deal.
I have a follow-up question though, how do you make the second hard drive auto-mount at startup?
Thanks a lot.

You can add an entry to /etc/fstab so it would be mounted automatically each time you boot.  If you're not sure how to edit it, tell me what partition is it, where do you mount it to (mountpoint), and what filesystem is it.

---

### Post by drworm01 on 2007-08-18
> **taurus said:**
> You can add an entry to /etc/fstab so it would be mounted automatically each time you boot.  If you're not sure how to edit it, tell me what partition is it, where do you mount it to (mountpoint), and what filesystem is it.

Partition: /dev/hdb
Mountpoint: /media/disk
Filesystem: ext3

Much appreciated.

---

### Post by taurus on 2007-08-18
> **drworm01 said:**
> Partition: **/dev/hdb**
Mountpoint: /media/disk
Filesystem: ext3

Much appreciated.

Have you created a filesystem on /dev/hdb because it cannot be /dev/hdb if you have?  It should be /dev/hdb1.

What's the output of this command from a terminal?

```
sudo fdisk -l
```
It is lower case letter l as in larry, not 1 or the pipe symbol--|.

---

### Post by drworm01 on 2007-08-18
Sorry, you're right, it is /dev/hdb1 I was grabbing the info from the partition editor instead of fdisk.

---

### Post by taurus on 2007-08-18
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/disk   ext3   defaults   0   1
```
Save the change.  And since you already have /media/disk (and if you don't, you need to create it first with "sudo mkdir /media/disk"), just reboot and see if /dev/hdb1 is mounted to /media/disk.

---

### Post by drworm01 on 2007-08-18
Perfect! It worked. Thank you for your help.

---

