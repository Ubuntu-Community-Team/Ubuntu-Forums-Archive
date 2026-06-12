---
title: "Getting into Windows Files"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-08-22
hello, 
i wanted to know if there was a way to get to my files in my windows partition from ubuntu? 

thanks

---

### Post by Lord Illidan on 2006-08-22
Try this link : [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Any probs, post them in this thread, pls.

---

### Post by birdbrain on 2006-08-22
Yes. This is the line for my windows partition in /etc/fstab

/dev/hda4       /mnt/windows            ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

This presumes that your windows partition is an ntfs partition. It will allow read, but I have not tried writing.

The other possiblity is to setup a seperate partition that you format as a fat32 parition and then you can mount it read/write.

---

### Post by atomkarinca on 2006-08-22
if you want to write to ntfs partitions: [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

---

