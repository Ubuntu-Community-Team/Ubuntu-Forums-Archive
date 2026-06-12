---
title: "Can't see my NTFS drive"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by felipebarroeta on 2007-09-01
Hello...

I downloaded an application that was supposed to let me write in my NTFS drive (ntfs-config), win vista. It happens now that I cannot only write, but I can't access the drive! First it said I wasn't root (a theme I dont finish to understand) I put the Pass like a million times.. didn't work of course, then I rebooted, and voila, i dont access my windows partition.

I might have done something wrong, but I do not know... If someone knows, please give me a hand here...

peace!

---

### Post by taurus on 2007-09-01
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Inxsible on 2007-09-01
Open a terminal and post the output of the following commands
```
sudo fdisk -l
``````
df -h
``````
cat /etc/fstab
```

---

### Post by felipebarroeta on 2007-09-01
Thank You Very Much Guys!:)

---

