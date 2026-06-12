---
title: "write to external hard drive"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Bloch on 2007-06-01
I used to have this sorted, but now after searching the forums for about an hour I still have figured it out.

I have a vfat external hard drive. It used to mount automatically in Dapper but doesn't in Feisty. I now mount it using the command

```
sudo mount -t vfat /dev/sda1 /media/EXTERNAL
```

which works fine except only the root user can write tot he external hard drive. 

How can I fix things so that the ordinary user (there's only me) can write to the drive?

Ideally automount would work properly again, but at least it works now for all my usb sticks

---

### Post by Inxsible on 2007-06-01
Use pmount for external drives.
```
sudo pmount /dev/sd* MOUNT_POINT
```
 
where mount point is the name of the folder and NOT the entire path
This will create the mount point under /media
for eg
```
sudo pmount /dev/sda1 EXTERNAL
```
then your drive will be mounted at /media/EXTERNAL. EXTERNAL should NOT already be an existing folder. pmount requires that it create the folder and does not use an existing one.
 
If you want to mount it to EXTERNAL, you will have to first unmount the drive and delete the folder
```
sudo umount EXTERNAL
sudo rmdir /media/EXTERNAL
```
 
My external HDDs automount after I use pmount

---

### Post by Bloch on 2007-06-01
It does indeed mount the drive.

But when I try to view it I get:

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of 'external'


I cannot seem to be able to change the permissions.
(by the way I have used a new name of a non-existent directory. pmount create the /media/external directory)

---

### Post by Inxsible on 2007-06-01
Try not to use spaces in your names for mount points. Will save you the trouble of using quotes around them.
 
for your permissions problem
```
sudo chown -R <your-username>:<your group> <device name>
```

---

### Post by Bloch on 2007-06-01
Thanks everyone.

I solved the problem by executing the command as normal user, without sudo. Just

pmount /dev/sda1 external

---

