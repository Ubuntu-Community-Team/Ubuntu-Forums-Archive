---
title: "Removing restrictions from NTFS partitions"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by EzEe on 2007-04-25
I am having problem with removing read only restrictions from ntfs partitions. When I check the permission of any folder on ntfs partition it shows me that the folder is owned by root and i don't have permission to change anything. Can somebody help me with it.

---

### Post by Wake Rider on 2007-04-25
Try this:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#head-62bb8324b93c2b77797bbd3e45493f08ad90a52c)

---

### Post by aberry5555 on 2007-04-25
In order for you to have read-write permissions on an NTFS disk you need to download and install "NTFS-3g" from synaptic. Once this is installed you can re-mount your HD as an NTFS-3g partition, and you should then have read-write permissions.

---

### Post by doomster on 2007-04-25
after you apt-get ntfs-config  use it with root pevillages  and you will have to enable both  tickers  "Enable Write support for internal/external device" . after hitting ok youre ook:)

---

