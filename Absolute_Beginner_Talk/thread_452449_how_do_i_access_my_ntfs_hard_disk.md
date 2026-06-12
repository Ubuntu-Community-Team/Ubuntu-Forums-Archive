---
title: "how do i access my ntfs hard disk"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by uzorp on 2007-05-23
some one plaese help me,i just started using edubuntu today after installing on one of my drives partition,the edubuntu is running fine.but i cant access my other hdd nor the ntfs partions on the hdd where i installed edubuntu.what do i do?

---

### Post by taurus on 2007-05-23
You need to mount it before you can access it.  I assume you also want to write to it.  Therefore, you need to install ntfs-3g and ntfs-config to configure it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by eentonig on 2007-05-23
ntfs-3g is very easy to install and activate on Ubuntu.

And allthough I use it regularly to move files to my work parttion. I do want to warn you that is is still a work in progress. I never had a problem with it, but I would take precautions just in case.

---

### Post by Inxsible on 2007-05-23
Go to Applications --> Add/Remove and search for ntfs.
 
It lists NTFS Configuration Tool. Select that for installation. After installing, Go to Applications --> System Tools --> NTFS Configuration Tool and select Write support for internal drives as well as external drives.
 
If you still can't write to those drives, it could be a permissions issue. Open a terminal  
Applications --> Accessories --> Terminal
then type in the following commands 
```

sudo chown -R <your username> <path to the drive>

```

---

