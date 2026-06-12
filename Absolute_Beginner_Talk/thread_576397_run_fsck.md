---
title: "run fsck"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-10-15
how do you run fsck on another hard drive.this hard drive has windows on it

---

### Post by mozetti on 2007-10-15
man fsck -- checkthe "See also" section and it should list the numerous different filesystem check programs available. I know there is one for FAT32 (i think its called dosfsck or something similar). I don't recall if there is one available for NTFS.

You can also check the link in my signature for an online directory of man pages.

---

### Post by hyper_ch on 2007-10-15
what do you want to do?

---

### Post by jonathan21 on 2007-10-15
I need to be able to repair hard drives.you know how somtimes a hdd will start sayoing unmountable disk volume.

---

### Post by hyper_ch on 2007-10-15
what kind of drive do you want to repair (what file system) and which OS do you want to boot for that?

---

### Post by jonathan21 on 2007-10-15
the file system ntfs.by the way thanks for your help really appreciate it.

---

### Post by vanadium on 2007-10-15
For repairing a ntfs filesystem, you still need windows, I am afraid. The ntfsfix program can fix an ntfs volume to some extent, but then sets the dirty flag so that windows will perform an ntfs consistency check on the next boot. Thus, despite write support with ntfs-3g, ntfs still is a format to keep away from if you are e Linux only user.

---

