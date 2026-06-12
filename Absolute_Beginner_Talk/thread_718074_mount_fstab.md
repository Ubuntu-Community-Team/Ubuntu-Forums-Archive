---
title: "mount fstab"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by flatbeard on 2008-03-07
Hello

I'm trying to mount a SATA harddisk into an existing (fresh) installation.
The SATA is freshly formatted with ext3 (I don't have a specific reason for choosing that over any other file system), and has recently been working fine.
When executing "sudo fdisk -l" this comes up:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x530a530a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/sdb: 9173 MB, 9173114880 bytes
255 heads, 63 sectors/track, 1115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19a37f0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1061     8522451   83  Linux
/dev/sdb2            1062        1115      433755    5  Extended
/dev/sdb5            1062        1115      433723+  82  Linux swap / Solaris

Disk /dev/sdc: 9173 MB, 9173114880 bytes
255 heads, 63 sectors/track, 1115 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19a37f0c

   Device Boot      Start         End      Blocks   Id  System
```

I've tried to add this to my fstab:
```
/dev/sda1 /dev/mnt/sda1 ext3 defaults 0 1 
```
And I've tried to replace the last "1" with a zero. I can't see the harddisk in computer:/// anymore - I used to be able to to just that. But since I entered the above to my fstab, it's gone.

Um ... then what do I do? :-k

---

### Post by ruy_lopez on 2008-03-07
don't mount in /dev/.

Create a folder in /media/ or /mnt/

```

sudo mkdir /media/sda1

```

Then change /etc/fstab
```

/dev/sda1 /media/sda1 ext3 defaults 0 1

```

Mount the partition
```

sudo mount /media/sda1

```

change the ownership, so you can access the mountpoint (replace username with your own username)
```

sudo chown username:username /media/sda1

```

EDIT: the partition should mount automatically on boot from now on.

/dev is a special folder. You typically don't write to /dev.

---

### Post by flatbeard on 2008-03-08
Wiii! It works! Thanks a lot. Medal! Medal! :) :) :)

I thought that /dev meant something like "devices". :roll:

---

### Post by herbster on 2008-03-08
It does, but you don't write to it as ruy noted.

---

