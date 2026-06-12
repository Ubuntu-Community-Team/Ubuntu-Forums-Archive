---
title: "Help Internal hard drive read only!"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Paul JR on 2007-08-17
i have second internal hard drive (ntfs) that is from my other computer and ubuntu wont let me write to it even when i am root any help is greatly appreciated 
btw i am not running dual-boot

---

### Post by merlinus on 2007-08-17
Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

### Post by Bachstelze on 2007-08-17
Moved to Absolute Beginner section per OP request.

---

### Post by Paul JR on 2007-08-17
> **merlinus said:**
> Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin
sorry it dident do any in termial
im a new user to linux but not that new

---

### Post by bodhi.zazen on 2007-08-17
To write to ntfs you need ntfs-3g

ntfs-config is a gui front end.

ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by Paul JR on 2007-08-17
> **bodhi.zazen said:**
> To write to ntfs you need ntfs-3g

ntfs-config is a gui front end.

ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

i have that program already
but it only works for "external" drives
i have a "internal" drive that is read only
the internal part is grayed out soo that program wont work

---

### Post by zeehat on 2007-08-17
That's not true.  ntfs-3g reads my internal HD perfectly.  Maybe it's the make of your HD that has problems.

---

