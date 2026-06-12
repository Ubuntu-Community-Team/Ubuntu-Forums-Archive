---
title: "Harddrive = permission denied"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Deus- on 2006-05-30
A quick question:
How to make my normal user to access the other harddrives I got?
I have managed to mount it without root's help but what about accessing it?

---

### Post by sharkey77 on 2006-05-30
777 or 755?

---

### Post by mlind on 2006-05-30
You should use *umask* parameter with mount command
here's what I've got on fstab for my NTFS share

```

/dev/sda5       /media/D        ntfs    ro,nls=utf8,**umask=0222**  0       0

```

---

