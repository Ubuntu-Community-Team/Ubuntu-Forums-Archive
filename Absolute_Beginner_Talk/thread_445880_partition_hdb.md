---
title: "partition hdb"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-16
hi, 

two hd's     40 gb 

ubuntu on hda , with swap 1G

partitioned hdb as hdb 1, 2, 3 all primary 

wanted to make them accessible , but when i run cat /etc/fstab, i only see hda


what's the best thing to do with my hdb 

make it extended (read about all this) then partition and logicals , (doesn't make sense !, or is making them primary the prob ?)

then try to make them accessible with 'chown'

:(

---

### Post by taurus on 2007-05-16
You first need to mount them before you can access them.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

