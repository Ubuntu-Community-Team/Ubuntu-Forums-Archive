---
title: "I dont have write permissions on my recently formatted disk? help!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by (chubbstar) on 2007-05-25
i have two internral hard drives (one to boot from and one for media). i just formatted my media disk to ext3 and now ubuntu cant use it! the drive is detected in feisty and i can mount it but it seems that only the root has permission to write on it.

how/where do i change the write permissions? and is there anything else i need to worry about to make this drive writable and automatically detected by my non-root user?

---

### Post by Ek0nomik on 2007-05-25
You can do it via terminal, but I presume you will want to do it graphically...

try:

```
gksudo nautilus
```

than right click on the folders on your newly created partition and change the permissions.

Is that what you're looking for?

---

### Post by (chubbstar) on 2007-05-25
yup that did it. excellent and thanks.

---

### Post by (chubbstar) on 2007-05-28
welp. things are almost perfect. i can now write and read the drive but i have to mount it in nautilus every time i log in. also, even though ive set all the write permissions appropriately i cant change the drives name (it simply mounts itself as 'disk')

how can i rename the disk and make it so that its automatically mounts from login?

---

### Post by ugm6hr on 2007-05-28
Try this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Ek0nomik on 2007-05-28
Here are some useful links for you:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

If you run into troubles or have questions, just let me know.

---

### Post by sdbkr on 2007-05-28
I have the same problem so i followed the link in the previous post to psychocats and followed the destructions and added 

/dev/hda5 /storage ext3 defaults 0 0 

i'm now getting a question in the terminal 

file name to write : /etc /fstab 
do i just press return or put a name in ? any ideas ?

---

### Post by ugm6hr on 2007-05-28
I think you missed a step:
sudo fdisk -l

Your drive WILL NOT BE /dev/hda5 - so don't do it.  Rethink. Start again.
It will almost certainly be either /dev/hdb1 or /dev/sdb1

---

### Post by sdbkr on 2007-05-28
Hi 
done what you suggest and get 

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4834    38829073+  83  Linux
/dev/hda2            4835        4998     1317330    5  Extended
/dev/hda5            4835        4998     1317298+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2480    19920568+  83  Linux

it still doesn't show up in /media, is that because i haven't given it a name ? but it does show up on the disk mounter on the panel. there's a folder in it called lost and found - do i leave that ?

---

### Post by sdbkr on 2007-05-28
also i still don't have write permissions on it

---

### Post by ugm6hr on 2007-05-28
Follow the instructions again with the following edit:

Substitute "/dev/hda5" with "/dev/hdb1" and "marie:marie" with "*yourusername:yourusername*"

---

