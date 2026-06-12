---
title: "cdrom file path"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-09-16
Whats the dvd/cdrom file path in ubuntu?

I'm using Dapper Drake and have two Lite-On DVD drives. Both work 100%, but when I try to open a DVD in VLC or configure my Parallel settigns I cannot figure where to send those programs to look for them. In windows they would be D: & E:

Thanks

---

### Post by Najand on 2006-09-16
They should be mounted in your /media or /mnt folder as two seperate folders...
If you see your /etc/fstab or just simply run 
```

"mount"

``` command you can figure out where your CD/DVD drives are mounted when they have the filesystem "iso9660" type.

---

### Post by redDEADresolve on 2006-09-16
Still cant get DVDs to play in VLC or send parallels to the right drive to read my DVD.

Thanks

---

