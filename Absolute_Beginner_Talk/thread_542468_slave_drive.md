---
title: "slave drive?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by jeramiahx on 2007-09-04
My slave drive was my secondary drive when I was running windows. I can access the drive and I can plat music ect. on it but I cannot write or delete anything of of it. It tells me I do not have authorization . It says it's user group is Root under properties? any ideas?

---

### Post by yabbadabbadont on 2007-09-04
Is it an NTFS drive?  If so, you will need to install and configure the ntfs-3g software.  Instructions for this can be found here: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Be sure to only follow the instructions that apply to your version of ubuntu.

---

### Post by sumguy231 on 2007-09-04
If it's formatted as NTFS, you'll need to install the ntfs-3g driver to write to it.

Edit: Beaten by seconds.

---

