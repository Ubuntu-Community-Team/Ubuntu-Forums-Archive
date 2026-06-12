---
title: "Fstab not mounting drive when user permissions are applied."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by JewKnowWho on 2008-03-14
When i try to add any permission to my mounted drive within fstab, it seems to prevent it from mounting at boot. I've tried both adding my uid and gid, and giving a umask=000

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32ce856c-65b8-49cc-8e0e-e3d8eed5cb44 /               ext3    defaults,erro$
# /dev/sda2
UUID=acd83ba4-a169-47f3-963a-411ccaba48ff none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda3       /home/oliver/sda3       ext3    defaults,uid=1000,gid=1000       0       0
/dev/sdb1       /home/oliver/sdb1       ext3    defaults,uid=1000,gid=1000        0       0
 
Any ideas?

---

### Post by freebios on 2008-03-14
login as root and apply the permissions by going to computer then checking the propertys on the drive, and change the permissions.  if you just want to auto mount the drive let me know.

---

### Post by taurus on 2008-03-14
Why not just modify those last two lines to these.

```

/dev/sda3 /home/oliver/sda3 ext3 defaults 0 0
/dev/sdb1 /home/oliver/sdb1 ext3 defaults 0 0

```
Then, change the ownership of /home/oliver/sda3 & /home/oliver/sdb1 so you can write to them anytime you want.

```
sudo chown -R oliver:oliver /home/oliver/sda3
sudo chown -R oliver:oliver /home/oliver/sdb1
ls -la ~
```

---

### Post by glennric on 2008-03-14
Do what taurus said.  The gid and uid options are not valid for ext3 partitions.  This is because ext3 partitions properly obey file permissions to begin with.  So using the chown will command will set them up the way you want.

---

### Post by JewKnowWho on 2008-03-15
Thanks for that, i'd previously formatted the drives in fat32 and it wouldn't let me chown any of the folders in there and i hadn't thought to try it after formatting in ext3. Just wasn't thinking, suppose thats what comes from using Windows all these years.

KissKiss

---

