---
title: "Cant find my harddisk"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2006-07-22
I did a upgrade from breezy to dapper.

I have three partitions one for windows .. one for my songs and movies and another one for ubuntu .... before teh upgrade i could see my harddisk and view teh contents but now i cant i open my harddisk from media >> hda1 >> o files  ... what do i do ... pls help

---

### Post by digby on 2006-07-22
Can you post the contents of /etc/fstab ?

---

### Post by theconley on 2006-07-22
It probably just didn't automount.

Try this (you will probably need to be root).

```
mkdir /media/hda1
mount /dev/hda1 /media/hda1/
```

~Conley

---

### Post by SkyNet2029 on 2006-07-22
as root
# mount
to see what is already mounted and where.
#mount -a
to mount it as listed in your /etc/fstab

Making a directory if the volume is just mounted in a different place would be a waste of time.

---

### Post by dead_man_walking on 2006-07-22
thnx guys .. i can see it now ... thnx for all this help that everybody is providing me

---

