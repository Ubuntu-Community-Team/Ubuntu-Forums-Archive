---
title: "restrictions on mounted harddisk partition"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by avenger on 2005-11-10
hi everyone
 noticed that there are restrictions on what i could do on hard disk partitions? 
i currently have a fat32 partition mounted. i noticed that i'm unable to download files from the internet straight into my mounted partition or un-tar archives into that partition. is it a real limitation or something that i did not do?

---

### Post by frodon on 2005-11-10
Maybe you're only able to do it as root if you didn't add the user parameter in your fat32 fstab line. Does your fat32 fstab line look like that ? : ```
/dev/hda2 /media/disk vfat user,auto,iocharset=utf8,umask=000 0 0
```

---

### Post by avenger on 2005-11-10
it actually looks like this. did i miss out anything?

sudo mount /dev/hda5 /media/linux/ -t vfat -o umask=000

---

### Post by frodon on 2005-11-10
Ok, make your fstab line look like the one i gave you, then run a "sudo mount -a" to remount all the partition, i think your problem will be solved.
Your line is not wrong but seems that it not allow a single user to handle the partition.

Let me know if it solved your issue.

---

### Post by avenger on 2005-11-10
hey it worked! thanks man

---

