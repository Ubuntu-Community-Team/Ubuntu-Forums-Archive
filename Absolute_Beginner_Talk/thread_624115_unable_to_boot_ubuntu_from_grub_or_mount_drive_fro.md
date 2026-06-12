---
title: "unable to boot ubuntu from grub or mount drive from live cd"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by truthbrush on 2007-11-26
OK so I have been waxing lyrical about ubuntu for the past few weeks and then I have had more issues this week that I know what to do with.  Solved the last one and sort of know how but I am lost now and can't find anything in the forums by searching.

Was using firefox......system crashed completely.....when restarted it got to ubuntu splash and bombed out to busybox1.3/ash command line and I can't get the system to boot from there.

I am running through the live CD.....It a dual boot Gutsy install with XP and ubuntu on separate drives and the unbuntu drive won't mount from live CD, whilst the windows hd does mount and is bootable still.

error for ubuntu drive is as follows when I try and view it with the live CD.....
"ubuntu unable to mount volume wrong fs type, bad option, bad superblock on hdb1.  missing codepage or other error."

anyone seen this before?  any suggestions?

---

### Post by spiderbatdad on 2007-11-26
Is your first boot option CD-ROM?

---

### Post by master_kernel on 2007-11-26
> **truthbrush said:**
> OK so I have been waxing lyrical about ubuntu for the past few weeks and then I have had more issues this week that I know what to do with.  Solved the last one and sort of know how but I am lost now and can't find anything in the forums by searching.

Was using firefox......system crashed completely.....when restarted it got to ubuntu splash and bombed out to busybox1.3/ash command line and I can't get the system to boot from there.

I am running through the live CD.....It a dual boot Gutsy install with XP and ubuntu on separate drives and the unbuntu drive won't mount from live CD, whilst the windows hd does mount and is bootable still.

error for ubuntu drive is as follows when I try and view it with the live CD.....
"ubuntu unable to mount volume wrong fs type, bad option, bad superblock on hdb1.  missing codepage or other error."

anyone seen this before?  any suggestions?
Harsh. Your drive is corrupted. How many hard drives do you have? hdb is usually code for the second HD you have. I think fsck may be able to fix it, you could try it from inside the Live CD.

---

