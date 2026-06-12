---
title: "Live CD and USB drive"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-06-19
80GB Western Digital USB 2.0 in NTFS. Should it show up on the desktop automatically?

---

### Post by FleetAdmiral74 on 2007-06-19
Well, the easy way that only takes 5 minutes would be to try. But I believe it will. Read only mind you, unless you install extra software for write access (which is available).

---

### Post by Nessa on 2007-06-19
I asked because I tried and it didn't. I went ahead and tested it on xp. Drive is working fine. So I guess it doesn't.

---

### Post by chamberlain2006 on 2007-06-19
On the Live CD, go to terminal (Applications>Accessories>Terminal) and type in 'lsusb'.  Could you please post that input?  Also, post the output of these commands:

fdisk -l
ls /dev | grep sd

Thanks, we should probably be able to get this working.

---

