---
title: "installing a second hard drive with 7.04"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by arno1991 on 2007-05-17
hello,

i just installed Ubuntu 7.04 Feisty Fawn, and first I had a 6.06 version of ubuntu installed
with the 6.06 installed, i found an easy to follow guide on the internet (google) to install a second hard drive. How can i install now a second hard drive or where can i found now a guide to install one? I searched already a lot to find one...

Please help

arno

---

### Post by taurus on 2007-05-17
What filesystem is that second harddrive?  If it's ntfs, then you probably need to install ntfs-3g so you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

