---
title: "Adding a HDD into Places&gt;Computer"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-28
In Dapper, I was able to see the 2nd HDD on Places>Computer. But in Edgy, it's not. How to fix it?

---

### Post by hotbrainz on 2006-11-28
Well to see any of the Hard disks or other media...it must be mounted in the /media folder in the root. Have you done that?

---

### Post by oliviacond on 2006-11-28
I done that (hundreds time already) but the problem is after next boot, the file in the /media gone. So, I have to mount it in the /media again to be able to access file. Pls help me...

---

### Post by hotbrainz on 2006-11-28
well how do you do this remounting thing? I mean what tool do you use?

---

### Post by oliviacond on 2006-11-28
This is the command I use :
> 
sudo mount /dev/sdb5 /media/windows/ -t ntfs -o nls=utf8,umask=0222


---

### Post by minisori on 2006-11-28
Add /dev/sdb5 /media/windows/ -t ntfs -o nls=utf8,umask=0222 to your /etc/fstab.

---

### Post by oliviacond on 2006-11-28
How?

---

### Post by taurus on 2006-11-28
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then, add this line to the end of it...

```

/dev/sdb5  /media/windows/  ntfs  nls=utf8,umask=0222  0  0

```

---

### Post by oliviacond on 2006-11-28
problem solved. :)

---

