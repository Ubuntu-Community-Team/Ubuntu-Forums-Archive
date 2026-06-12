---
title: "Cannot find shared FAT32 partition in kubuntu"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by hyperpsyched on 2006-02-04
May as well post this here. My problem is that I put aside a little shared space on my hd in FAT32 but I cannot seem to find it in kubuntu. No hd[X] in /dev/ for drives or anything. Do I need to do anything special to access the FAT32 partition?

---

### Post by Parkotron on 2006-02-04
Try the Disk & Filesystems control module.

1. Open up SystemSettings or KControl.
2. Under System Administration open Disk & Filesytems.
3. Click the Administor Mode button and give your password.
4. Look for your partition in the list. 
5. If it is there and already has a mount point you can change it with the Modify button. If it is there and has no mount point you can create one with the New button. If it isn't there at all, you've got much bigger problems

---

### Post by cotcot on 2006-02-05
do you see your fat partition in the list when you do :  sudo fdisk -l in terminal ?

If yes then it should be possible to mount it. See ubuntu unofficial guide(s) : for example : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by hyperpsyched on 2006-02-05
The advice totally worked... woo hoo.

Thanks to both of you, I am now at peace at least until the next problem reares it's many tentacled head.

---

