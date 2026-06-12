---
title: "usb hard drive and user permissions"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by gusoceros on 2008-03-26
Hi all, I have a usb hard drive I would like all users to have permission to read.  How do I setup the permissions of the usb hard drive so that all the users have the permission to read and access what is there?

Thanks

---

### Post by nitro_n2o on 2008-03-26
if your usb is NTFS then 
sudo apt-get install ntfs-config 

which is a gui to help you set up permissions

have a look at this post [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by gusoceros on 2008-03-26
OK- that is good to know, I dont think I was clear enough in my question however.

I can access and write to my USB HD logged in as admin- however, none of the other users have access to this USB HD when they try to access it when they are logged in.  It seems, only the admin user has abilities to read the USB HD, either that, or it is mounted on that user, and something else needs to happen to allow the other users the ability to read and write to the disk as well.

G

---

### Post by gusoceros on 2008-03-27
> **gusoceros said:**
> OK- that is good to know, I dont think I was clear enough in my question however.

I can access and write to my USB HD logged in as admin- however, none of the other users have access to this USB HD when they try to access it when they are logged in.  It seems, only the admin user has abilities to read the USB HD, either that, or it is mounted on that user, and something else needs to happen to allow the other users the ability to read and write to the disk as well.

G

ANyone have an idea how I can get the various users on this PC to have access to the USB Hard Drive??

---

### Post by DBrocks on 2008-03-27
> **gusoceros said:**
> ANyone have an idea how I can get the various users on this PC to have access to the USB Hard Drive??


```
sudo chmod 444 THELOCATIONOFWHERETHEDRIVEISMOUTNED
```
This will allow all users to read the drive, but not write. If it is a NTFS drive, writing is more complicated. But if you need just read support, that should do it.

Good Luck!

---

