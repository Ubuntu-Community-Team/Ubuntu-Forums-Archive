---
title: "Need acces to another drive on my computer"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by aoiz on 2006-05-30
I want to access drive D: from my main drive C:
->The problem is: D: runs on Win 98
therefore, Ubuntu does not recognise it as a drive or location

Is there any possibility to find and access D:?

---

### Post by frodon on 2006-05-30
The answer is there : 
[http://doc.gwos.org/index.php/BreezyGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://doc.gwos.org/index.php/BreezyGuide#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by zvezdogled on 2006-05-30
Usually you can. Here is what you should do:
1. e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows
2. to mount windows partition:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
3.to unmount it:
sudo umount /media/windows/

that is asuming that you have a NTFS windows partition. 
Just described i found on a page:
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)
i would recomend it tou you if you want to find more abount mounting windows partitions and many more. It's a realy nice page.

---

