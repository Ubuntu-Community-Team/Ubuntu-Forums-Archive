---
title: "[SOLVED] Mount Command Problems"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by jdg.gehrig on 2007-08-24
I can't figure out how to mount my Network Drive. When I use the mount command:

sudo mount //mybookworld/public  /home/*user*/Desktop/NetworkDrive/

the folder is mounted correctly and I can read the files but I can't get a non root account to write to the drive is there an option that will allow this?

Thanks in advance,     John

---

### Post by newlinux on 2007-08-24
you probably want to unmount it and try:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

(you need the dmask and fmask)

---

### Post by jdg.gehrig on 2007-08-24
Thanks That Worked!

also, i just used the dmask and fmask given in the example

---

