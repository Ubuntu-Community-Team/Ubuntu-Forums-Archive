---
title: "Can I use UB tools to create windows 7 recovery disk?"
date: 2012-05-21
forum: Any Other OS
---

### Post by mringer on 2012-05-21
I have a new PC from Dell: one disk, parted says:

```

1049K -- 106M     primary     fat16       flag diag    used 10M
106N  --  15G     primary      ntfs       flag boot    used  5G
rest of disk      primary      ntfs       no flag      used 17G

```


Dell provide a process to make a recovery disk. This ran with no 
visible error, but there seems to be no way to find out if the 
recovery disk will work until the day when I have to use it for 
real. 

Please is there a procedure to boot from a live CD and use Ubuntu
programs to make backups? I understand that if you simply mount 
these partitions and use tar to backup, then after restoring, the
restored disk is not bootable.

Thank you.

---

### Post by rai4shu2 on 2012-05-21
You might have a look at Clonezilla live: [http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

---

