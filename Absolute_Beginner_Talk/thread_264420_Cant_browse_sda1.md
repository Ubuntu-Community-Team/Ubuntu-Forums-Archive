---
title: "Cant browse sda1"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by gazzard41 on 2006-09-24
The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-sda1".

not sure if this is mount problem can u help

---

### Post by kidders on 2006-09-24
What are the mount point's permissions like?

---

### Post by bodhi.zazen on 2006-09-24
Mount point permissions do not matter, they are changed at the time of mount (try it and see).

How did you mount the partition?

I advise```
sudo mount <dev> <mount_point> -o user,rw
```

You may also want to add a line in fstab.```
<dev> <mount_point> auto auto,user,rw 0 0
```
This will allow you to mount and use the partition as a user.

---

### Post by kidders on 2006-09-24
> Mount point permissions do not matter, they are changed at the time of mount (try it and see).Lol well yes... taking a look *after* the device is mounted would be sensible.

Two further suggestion for the /etc/fstab entry:

[LIST]
[*]Changing "auto" to "noauto" would prevent the partition being automounted by root during boot. (Only really applies to FAT/NFTS partitions though.)
[*]Changing "user" to "users" to avoid confusion. This would allow "umount" to be performed by users other than the one that performed the "mount".
[/LIST]

bodhi.zazen may want to vet those suggestions first though :-)

---

### Post by bodhi.zazen on 2006-09-24
> **kidders said:**
> Lol well yes... taking a look *after* the device is mounted would be sensible.

Two further suggestion for the /etc/fstab entry:

[LIST]
[*]Changing "auto" to "noauto" would prevent the partition being automounted by root during boot. (Only really applies to FAT/NFTS partitions though.)
[*]Changing "user" to "users" to avoid confusion. This would allow "umount" to be performed by users other than the one that performed the "mount".
[/LIST]

bodhi.zazen may want to vet those suggestions first though :-)

Both are correct and good suggestions.

auto/noauto is dealer's choice.

user is more secure then users. Again, dealer's choice.

And I'm just a noobie... :)

---

