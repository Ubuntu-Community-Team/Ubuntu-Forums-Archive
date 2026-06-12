---
title: "partition's rename"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by housam on 2006-12-04
G'day All,

How could I rename all the partitions under Dapper ( I have dual boot )

---

### Post by frolle on 2006-12-04
Can't gparted do that?

---

### Post by housam on 2006-12-04
No, I didn't find a way to do it through Gparted.

---

### Post by Bachstelze on 2006-12-04
What do you mean "rename" ? Change the /dev/hdaX ? I don't think it's possible and even if it was, I can't see the use of it.

---

### Post by housam on 2006-12-04
What I mean is to change the volume name i.e. from sda1 to Games.

---

### Post by petteriIII on 2006-12-18
You must know this by now but here you are anyhow:

Every partition has a name. It is 1-16 places long. It may be given with command: sudo tune2fs -L name /dev/<devicename> . Examples of usage:
in fstab: LABEL=ubuntudata  /home/petteri/data ext3 defaults,user_xattr   0     0
in menu.lst: kernel  /boot/vmlinuz-2.6.17-10-generic root=LABEL=petteri ro splash
- notice: user_xattr  in fstab

Ubuntu honors the use of name, but it prefers UUID that is 32 places allways. When you use them, Ubuntu takes care to search what disk they are on; if eg. you put USB-disk on during operation the already 'given' devicenames may change. But it has also dangers: eg. if there are more than one partition with the same name it may even lead to a situation that you are using wrong disk without been told about it.

UUID is defined by partition-program. You can only look at what it is in the directory: /dev/disk/by-uuid -> and by right-clicking any filename and choosing preferences you can see its devicename.

---

### Post by housam on 2006-12-18
Thank you for the explanation. I already renamed the partitions by remounting them and changing the letters to names through fstab.

---

