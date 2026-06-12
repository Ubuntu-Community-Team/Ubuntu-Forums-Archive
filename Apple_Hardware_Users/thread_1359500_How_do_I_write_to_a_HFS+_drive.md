---
title: "How do I write to a HFS+ drive?"
date: 2009-12-19
forum: Apple Hardware Users
---

### Post by Virtualboxbuntu on 2009-12-19
I want to do a fresh install of Ubuntu so I want to back up all my important data. The only backup device I have is a HFS+ (no journaling) formatted external hard drive. No matter how I try to mount it, it says that it's a read-only file system. What do I do?

---

### Post by phillw on 2009-12-19
Hi 

[http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/](http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/)

It's right near the top of the article as to how to enable rw

Regards,

Phill.

---

### Post by Virtualboxbuntu on 2009-12-19
Thanks. Is there a way to just mount the hard drive once (which I want to do), rather than having it in fstab? And would a USB drive even work properly with fstab?

---

### Post by phillw on 2009-12-20
> **Virtualboxbuntu said:**
> Thanks. Is there a way to just mount the hard drive once (which I want to do), rather than having it in fstab? And would a USB drive even work properly with fstab?
Hi,

I'm not familiar with hfs filetypes, but the general mount command using the -t parameter *should* mount it.

Using the above example of **/dev/sda3** being the partition or drive to be mounted and **/mnt/common** being where you want to mount it to, then, in theory (!!)

```
sudo mount -t hfsplus /dev/sda3 /mnt/common
``` 

Will mount the device. As to what permissions it will give - I'm sorry I don't know. I did read that he had to ```

sudo chmod -R 777 /mnt/common
``` To get both Mac & Ubuntu to read & write the files

Hope that points you in the correct direction.

Regards,

Phill.

---

### Post by tom4everitt on 2009-12-22
All you need to do is to mount and unmount your drive in OSX. The cause of the problem is a flag that is set when its not unmounted properly, forcing it to be mounted read only. Mounting and unmounting in OS X will reset this flag.

---

