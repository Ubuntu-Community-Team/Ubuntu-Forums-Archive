---
title: "Is it possible to have a partition which is accessible to Linux and Windows?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-28
I have a partition for Linux and another for Windows. I was thinking if it is possible for me to create a partition which is accessible for both Linux and Windows. That way, I can play my songs on the two OSs and I can easily share information between Linux and Windows.

Is that possible? 

If it is, how can I do it?

---

### Post by Hossie on 2007-01-28
Just use FAT32 as filesystem.

---

### Post by kinematic on 2007-01-28
yes...it's possible.
format the partition as fat32.
windows will recognize it automatically but you'll have to mount it in ubuntu by editing /etc/fstab.
if you do forum search for "mount fat32" you should get the info you need.

---

### Post by housam on 2007-01-28
You can access ubuntu files through windows by installing [this driver]("http://www.fs-driver.org/")
and also the windows files through ubuntu by [mounting them]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by addict3d on 2007-01-28
Windows partitions are accessible under linux (FAT32 as well as NTFS). So, using windows partitions itself you can share information between the two OS's. You have to mount the partition in a location under linux using 
sudo mount <partition-name> <location> 
Thats it
Or there is another way. explore2fs is a program for accessing linux partitions in windows.. Get it here : [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm).. I think you cant write to the linux partiion in windows using this though..

---

### Post by thesmartace on 2007-01-28
You can format the drives to FAT32 and they should be automatically detected by both OSs.

If you want to see your linux partition (if its EXT3) in windows then you can get a driver from [http://www.fs-driver.org/]("http://www.fs-driver.org/").

---

