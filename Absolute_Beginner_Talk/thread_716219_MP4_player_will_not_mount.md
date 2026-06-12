---
title: "MP4 player will not mount"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by giddy1945 on 2008-03-05
jacktheripper@jacktheripper-desktop:~$ sudo fdisk -l
[sudo] password for jacktheripper:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47936   385045888+  83  Linux
/dev/sda2           47937       48641     5662912+   5  Extended
/dev/sda5           47937       48641     5662881   82  Linux swap / Solaris
jacktheripper@jacktheripper-desktop:~$ 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Executing the command,"mkfs.vfat /dev/name -I", is what I did wrong.  The result is above.  I think I need to buy a new mp4 player...unless YOU can help me.

Thanks.

---

### Post by giddy1945 on 2008-03-10
bump

---

### Post by sayakb on 2008-03-10
> **giddy1945 said:**
> bump

```
sudo mount -t /dev/name -o force
```

---

### Post by giddy1945 on 2008-03-10
i may need to be more clear.  when i did the command "mkfs.vfat /dev/name -I", i erased my mp4 player all together.  the "sudo fdisk -l" command reveals my hard drive.  I cannot remember the name of my mp4 player, so i do not know waht to call it when i use "sudo mount -t /dev/name -o force".  my mp4 player just displays an hour glass icon on its screen, and it is not detected.  i screwed it up some how.

although i may be missing your point, i did read everything your command illuminated (instructions and so forth which i do not understand).

thank you for the reply.

---

