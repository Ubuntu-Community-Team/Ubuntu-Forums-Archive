---
title: "How can I find my other Windows partitions(ntfs) on Ubuntu"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by koprioni on 2006-12-02
How can I find my other Windows partitions(ntfs) on Ubuntu and the opposite?
Thnx very much.I m totally new to Linux(ss yesterday installed) and i have a lot of questions but firt with this.
Sorry for the double post.

---

### Post by Ocxic on 2006-12-02
open a terminal a type "sudo fdisk -l" thats an L lowercase.
and it'll give you a list of your partitions similar to this:
```

ikrel@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          18      144553+  83  Linux
/dev/hda2              19       14946   119909160   8e  Linux LVM

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   8e  Linux LVM

```

if you want to mount an NTFS partition then the command is:
"sudo mount /dev/hda /mount/point -t ntfs -o nmask=0222"

replace hda with the partition/drive you wish to mount, and /mount/point to where you want it mounted.

---

### Post by koprioni on 2006-12-02
mount: mount point /mount/point does not exist
what am i doing now...?why this doesnt work?

---

### Post by jingo811 on 2006-12-02
[I]Aye, follow me ol' salty dog and Me will show you the way!
Just click on my sign signature. [/I]

Begin from step 6.  And post your future questions in here and NOT in my Tutorial thread!

PS.
In Dapper Draker 6.06 all my Windows partitions got mounted automatically and placed on the desktop without me needing to lift a finger.
Maybe you should install Draker.

---

### Post by taurus on 2006-12-02
> **koprioni said:**
> mount: mount point /mount/point does not exist
what am i doing now...?why this doesnt work?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by koprioni on 2006-12-02
thnx taurus.the link helped me a lot.
Now can anyone tell me why my system hungs when i try to restart shut down or logoff?
Thnx!

---

### Post by Chinkostu on 2006-12-02
you need to make a directory to mount it to before using that command with

```
sudo mkdir /dev/DEVICELOCATION
```

where device location would be hda, hdab, hda1 etc etc. you should be able to go into the disks and find the name of it (i would be more clear, but im not in ubuntu at the moment so sorry!)

as for EXT support in windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)

i use that, it helps if i need to fix my Xorg.

---

