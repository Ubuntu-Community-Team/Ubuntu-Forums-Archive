---
title: "Automounting raid partition using dmraid"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Mongo5000 on 2007-08-15
So i've spent some time and now can mount my raid partition just fine.

What I want to do is have it automatically mount when I start up.  I've read that I have to edit my fstab file and I added what I thought would work but it doesn't mount when I bootup.

this is how I mount the partition normally, how do I get it to automatically mount when I startup?
```
sudo mount /dev/mapper/sil_afabahdcajbd6 /mnt/raid/ -o uid=stephen,gid=users
```

---

### Post by Mongo5000 on 2007-08-15
Wow this went down the list fast, anybody?

---

### Post by kevstar31 on 2007-08-15
add the following line to /etc/fstab as root:
/dev/mapper/sil_afabahdcajbd6 /mnt/raid/ auto uid=stephen,gid=users 0 0

---

### Post by Mongo5000 on 2007-08-15
Awesome, that did the trick!

Thanks a million

---

### Post by Mongo5000 on 2007-08-15
One last thing, I don't seem to be able to write to the ntfs raid partition.  I can read, just can't write, how can I set this up?

---

### Post by Mongo5000 on 2007-08-15
Update

I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=526196&highlight=write+to+ntfs") and it works.

 But I still need to sudo mount -a whenever I reboot.  Its not an issue, but would be nice if I didn't have to do that every time.

---

### Post by kevstar31 on 2007-08-16
Try this line instead:
/dev/mapper/sil_afabahdcajbd6 /mnt/raid/ auto uid=stephen,gid=users,rw 0 0

---

