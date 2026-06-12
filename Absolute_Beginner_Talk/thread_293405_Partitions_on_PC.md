---
title: "Partitions on PC"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-05
Hi everybody.

I'd like to know the partitions of my Hard Disk. Is there any command I can give form terminal to know it, please?
Thanks.

---

### Post by hearnden on 2006-11-05
Here are two you can try:

```

$ df

```

Lists mounted partitions and how much is free on each etc.

```

$ sudo fdisk -l

```

Lists the partitions on your hard disk (even unmounted ones).  Use 'sudo fdisk -l /dev/xxx' to query partitions on device /dev/xxx.

---

### Post by helphope on 2006-11-05
OK.
Thanks
:)

---

