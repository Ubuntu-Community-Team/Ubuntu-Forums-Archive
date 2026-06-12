---
title: "How do I edit the file /etc/fstab ?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by bear54 on 2008-03-10
When I try to edit the file **/etc/fstab** it says the file is a read only file. In the terminal I am logged in as root. I have a windows external HD that I am trying to make rw instead of ro. I have read that if I change ro to rw that my external hard drives will be read write instead of read only. I use Ubuntu 7.04 as my OS. If anybody can help me with this I would really appreciate it.
   Eric

---

### Post by MegaJim on 2008-03-10
Is the partition NTFS?  If so you can use ntfs-config to automatically setup your fstab to be read+write

```
 sudo apt-get install ntsf-config
```

---

### Post by bear54 on 2008-03-10
The external drive is vfat 32.
    Eric

---

### Post by kaens on 2008-03-10
> **bear54 said:**
> When I try to edit the file **/etc/fstab** it says the file is a read only file. In the terminal I am logged in as root. I have a windows external HD that I am trying to make rw instead of ro. I have read that if I change ro to rw that my external hard drives will be read write instead of read only. I use Ubuntu 7.04 as my OS. If anybody can help me with this I would really appreciate it.
   Eric

If /etc/fstab is read only, the command

```

chmod +rw /etc/fstab

```

should make it read/write.

Note that changing the read / write permissions of /etc/fstab will not change the read / write permissions of your drive.

Also, I'm not sure why /etc/fstab would be read-only to root anyhow.

---

### Post by ferdostar on 2008-03-10
> **bear54 said:**
> When I try to edit the file **/etc/fstab** it says the file is a read only file. In the terminal I am logged in as root. I have a windows external HD that I am trying to make rw instead of ro. I have read that if I change ro to rw that my external hard drives will be read write instead of read only. I use Ubuntu 7.04 as my OS. If anybody can help me with this I would really appreciate it.
   Eric

Sorry, but have you try with
```
sudo gedit /etc/fstab
```

---

### Post by bear54 on 2008-03-10
I used the following suggestion and it worked great but when looking at the /etc/fstab file I was not sure what I should do and do not want to cause my computer to not boot-up by making a mistake. Maybe someone could help me out with this. Thanks to all for your help.
Eric

**sudo gedit /etc/fstab**

etc/fstab - file

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ea346f1e-06df-4587-86cf-9b52828cefce /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=2156c3ad-af9a-46ff-ba16-05445b36b445 /media/sda4     ext3    defaults        0       2
# /dev/sda1
UUID=14F0E970F0E9590E /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=45eb2f08-09ac-4f71-9dc0-b99ccf8206c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/B]

---

### Post by Duck2006 on 2008-03-10
This may help with editing your fstab.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bear54 on 2008-03-11
duck2006
Thanks for the info (link) it was just what I was looking for! My drive works great. I appreciate it very much.
  Eric:)

---

