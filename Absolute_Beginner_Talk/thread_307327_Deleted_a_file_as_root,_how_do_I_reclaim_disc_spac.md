---
title: "Deleted a file as root, how do I reclaim disc space? [Resolved]"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-11-26
I just deleted a 4.1gb VMware file as root, but I have not reclaimed that disc space. How can I reclaim that space?

---

### Post by shin on 2006-11-26
Deleted, how exactly? Command line sudo rm? GNOME/KDE/anything session and right click->delete? Was it user or root session?

Oh and did you change default filesystem during installation or is it ext3?

---

### Post by happy-and-lost on 2006-11-26
Deleted from a root nautilus by pressing "Delete". My filesystem in ext3.

---

### Post by tageiru on 2006-11-26
> **happy-and-lost said:**
> I just deleted a 4.1gb VMware file as root, but I have not reclaimed that disc space. How can I reclaim that space?

Is there a process that still has the file opened? The kernel will not reclaim the space until all file descriptors have been closed.

fuser should be able to tell you if some process is still holding a file descriptor.

EDIT: Missed that you used nautilus, if the file has ended up in roots trash you should be able to delete the file from /root/.Trash/

---

### Post by shin on 2006-11-26
also check your thrash bin, dunno about nautilus but in kde delete normally just moves files to Thrash bin.

and as tageiru said, if some process is still using this file, space wont be reclaimed until it's done

---

### Post by happy-and-lost on 2006-11-26
Never mind. I've just found the /home/root/.Trash file and emptied it.

---

