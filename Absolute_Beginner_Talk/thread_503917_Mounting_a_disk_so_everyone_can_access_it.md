---
title: "Mounting a disk so everyone can access it"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jonl on 2007-07-18
Can anyone please tell me how to mount a disk (dev/sdb1) so everyone in my network can access it?

Thanks JonL

---

### Post by sab0403 on 2007-07-18
You have to have a network server service up first before you can do that. If you're using an all-linux network, you can use [NFS]("http://doc.gwos.org/index.php/NFS_Easy_Way"); otherwise, you'll have to use [Samba]("https://help.ubuntu.com/community/SettingUpSamba").

The tutorials linked to explain how to set these services up, as well as mounting devices (both in the host and the guests).

---

