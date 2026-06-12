---
title: "Don't have permission to my Own Hard Drive!!!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by socngill on 2007-05-19
Hi all.

I have just installed Amule (to replace EMule from my Windows install) and the folders it told me held my Temp and Incoming files doesn't exist.  So instead I pointed the program to my already existing folders on my Spare Drive.  Now I can't even run amule as it come up with this error:

Permissions on the aMule temp directory too strict!
aMule cannot proceed. To fix this, you must set read/write/exec
permissions for the folder '/media/hdb1/Temp'

Now, I can't find anyway of changing the permission details - can anybody help?  If anybody can help and it involves the dreaded TERMINAL can they write exactly what I need to write to get it to work - pretty please!

The folders are located:
/media/hdb1/  

and they are Temp and Incoming but to be honest what I really need is to change the permission for the entire hard drive - named Spare (if that helps ;) )

---

### Post by Outrunner on 2007-05-19
```
sudo chown username:group /media/hdb1/Temp
```

I think your group would be the same as your username if you didn't change it.

And DO NOT try to change permissions for the whole HDD, that's a VERY bad idea.

---

### Post by taurus on 2007-05-19
What filesystem is /dev/hdb1?  If it's ntfs, then you need to install ntfs-3g before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

```
sudo fdisk -l
```

---

### Post by socngill on 2007-05-19
Thanks for that - very quick :)

I have done it and it reads:

chown: changing ownership of `/media/hdb1/Incoming': Read-only file system

But I still can't change the file permissions?  And so still can't access Amule.  Do I need to do something else as well or am I doing it wrong?

Thanks again.

---

### Post by socngill on 2007-05-19
> **taurus said:**
> What filesystem is /dev/hdb1?  If it's ntfs, then you need to install ntfs-3g before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

```
sudo fdisk -l
```

Absolute superstars!!!  Thanks to both of you for your quick and fantastic help!

You can be sure I'll be back...

---

### Post by socngill on 2007-05-22
I have since found another folder which I can't mke changes to the Pixmaps folder that holds all the icons.  I wanted to add an icon image to my launcher but none of the images already there were what I wanted, so I tried moving an image across but I got the "you are not the owner of this file" message.  When I tried to "browse" for an image saved elsewhere it didn't seem to recognise anf image files I have on my PC?  So firstly is there a way of preventing this message from ever appearing -say by changing the owner of everything to me (instead of i assume the root?).  And secondly why won't it allow me to select an image from elsewhere?

Thanks.

---

### Post by Outrunner on 2007-05-22
```
gksudo nautilus
```
to start Nautilus in super user mode(so you can copy files without restriction). Be careful and don't try to play with system files while using Nautilus in super user mode!

---

### Post by socngill on 2007-05-22
That's done the trick - many thanks :KS

---

### Post by eoghanmurray on 2007-05-26
I have a similar problem. I have one external drive*, and an internal drive**.

* External hard drive partitioned into two partitions:
100.0GB - ext3
400.0GB - NTFS

** Internal Hard Drive in one partition:
80.0GB - NTFS

For the external drive*, I can access the files, but permissions are read-only and set to 'root'.
For the internal drive**, I 'am not privileged to mount this volume'.

Any help?
Thanks for your help.

---

