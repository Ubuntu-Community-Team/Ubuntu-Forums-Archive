---
title: "LINUX pathway help"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by jackpetrilli on 2008-01-13
I'm doing something (too involved to explain here) that progresses me to the point where a script says it can't find
/boot/grub/grub.conf

I feel if I could give it an absolute path (that includes the disk drive), it just might work.

In Dos/Windows, for example, I would put D:\boot\grub\grub.conf where D: would be the drive.

Now I know Linux doesn't use letters for drives. Would something like /etc/dev/sdb2/boot/grub/grub.conf work?
or maybe just sdb2/boot/grub/grub.conf?

(Please note that I know Linux would call Disk2,partition2: hd1,1)

Does anyone know how I would give an EXACT absolute path command to the /boot/grub/grub.conf of disk2 partition2 (which LINUX has recognized as sdb2)?

- Jack

---

### Post by p_quarles on 2008-01-13
Ubuntu doesn't use a grub.conf file, so it simply doesn't exist.

Also, in this case /boot *is* the absolute file path. If it were on its own partition drive, that would be the mount point in your filesystem.

---

### Post by oldos2er on 2008-01-13
The Ubuntu equivalent of grub.conf would be /boot/grub/menu.lst .

---

