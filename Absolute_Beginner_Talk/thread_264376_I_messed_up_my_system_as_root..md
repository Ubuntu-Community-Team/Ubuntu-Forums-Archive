---
title: "I messed up my system as root."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by prototype_angel on 2006-09-24
I logged on as root after enabling it, because I could not access my data on ntfs drives. I tried mounting them over and over again but no use. I tried logging in as root and changing the permissions of the partitions in the tmp directory to get hold of all my music(collection was on ntfs, moved from windows). I allowed my normal user to access it through the gui, which it refused to do as it was write protected. Now I can't access it as root also to copy music.

Can someone please tell me links on how to enable ntfs read/write support. I know read is inbuilt into kernel, but I can't get my data.

Thanks.

---

### Post by comppsyco on 2006-09-24
Try reading this in the wiki to mount NTFS:

[https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)

NTFS writing is here:

[https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)

---

### Post by prototype_angel on 2006-09-24
> **comppsyco said:**
> Try reading this in the wiki to mount NTFS:

[https://help.ubuntu.com/community/Au...ountPartitions](https://help.ubuntu.com/community/Au...ountPartitions)

NTFS writing is here:

[https://wiki.ubuntu.com/Lkraider/NtfsFuse](https://wiki.ubuntu.com/Lkraider/NtfsFuse)
thanks for the quick reply. that helped

---

