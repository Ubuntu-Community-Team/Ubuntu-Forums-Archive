---
title: "permanently mount windows hard drive"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by y3ahright on 2006-10-08
for some reason ubuuntu has decided not to mount my windows hard drive for me so i have to put in ```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
``` everytime i shutdown i have to re-enter it.. is there a way to  permanently mount my windows hard drive??

---

### Post by divague on 2006-10-08
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

