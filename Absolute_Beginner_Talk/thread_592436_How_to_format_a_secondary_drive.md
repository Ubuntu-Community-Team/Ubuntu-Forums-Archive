---
title: "How to format a secondary drive"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-26
I have a 200 GB drive as my back up and extra space.  its formatted to NTFS and id like to format the whole thing to fat32 so i can write to it.  im running x64 fiesty.  any help would be awsome.  

thanks for your time.

---

### Post by taurus on 2007-10-26
Install gparted and use it to format it to vfat.

```
sudo apt-get update
sudo apt-get install gparted
```
It now should be in System -> Administration.

Keep in mind that you cannot write to vfat/fat32 with a file larger than 4GB.

---

### Post by Orbital75 on 2007-10-26
If you upgrade to 7.10 you'll be able to read and write to your NTFS drive.
This feature is included in 7.10.

---

