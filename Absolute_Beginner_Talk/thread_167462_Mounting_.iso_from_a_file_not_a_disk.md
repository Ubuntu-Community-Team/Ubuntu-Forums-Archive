---
title: "Mounting .iso from a file not a disk"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-04-28
Is it possible to mount a .iso from a file if I don't have the physical disk.  If so, what would be the syntax?

---

### Post by kabus on 2006-04-28
mount -o loop *yourfile.iso* *mountpoint*

---

### Post by echo $USER on 2006-04-28
Thanks.

---

