---
title: "[SOLVED] Can't Copy Files to USB Drive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-10-26
I am trying to copy files to my thumb drive, but get denied stating that I don't have permissions. 

I have read all of the threads...

I know why this is... all windows fat32 and ntfs partitions are mounted as read-only

My stick is FAT32... I tried formatting it as NTFS in windows, but it does not give me the option. 

the partition is 

/dev/sdb1

But for kicks...
I have tried adding this to fstab as 

/dev/sdb1 /media/disk ntfs-3g defaults,locale=en_US.utf8 0 0

but then I get the error telling me that the usb drive is not NTFS... which of course I know that

Can I format this drive in linux?

---

### Post by danm-koder on 2007-10-26
instead fo trying to mount it as ntfs, why don't you try to mount it as vfat with r/w permissions??

---

### Post by philinux on 2007-10-26
[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

however of you format it as vfat as suggested you'll be able to read/write from windows or linux

---

### Post by Nachtengel on 2007-10-26
next to the 'defaults' line in your fstab, you can add ',r,w' which adds read and write permissions.

Also you can just try using chown on the directory it's mounted as to give yourself permission to read, write and execute.

---

### Post by tech9 on 2007-10-26
> **philinux said:**
> [http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

however of you format it as vfat as suggested you'll be able to read/write from windows or linux

Thanks philinux...

formatting as vfat did the trick!

Cheers! :)

---

### Post by philinux on 2007-10-26
Ok you can mark the thread SOLVED then ...

---

### Post by tech9 on 2007-11-15
> **philinux said:**
> Ok you can mark the thread SOLVED then ...

Sure thing

---

