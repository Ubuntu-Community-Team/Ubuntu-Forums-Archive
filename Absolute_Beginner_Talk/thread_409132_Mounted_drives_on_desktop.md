---
title: "Mounted drives on desktop"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Feck on 2007-04-14
Hi! I'm wondering how to get mounted drives and partitions to stop showing up on my desktop by default. Ideally, I'd like to be able to choose which ones actually appear on the desktop when they're mounted, but if it's all or none, I'll settle for none. Any suggestions?

Cheers,
Feck

---

### Post by Rui Pais on 2007-04-14
hi,
to show/hide all:
on a terminal type 
```
gconf-editor
``` 
go to: apps->nautilus->desktop
check/uncheck volumes_visible key.

To make some visible and others not, you need to change the mount points.
Those that appears on desktop are the ones mounted on /media. 
You can edit the file /etc/fstab, comment the entrys you don't want to appear or make them mount somewhere else, like /mnt/ instead of /media.

hth

---

### Post by Feck on 2007-04-14
when trying your first method: gconf -editor

I get an error message saying the gconf command wasn't found

About your second method, the editing of the fstab file

If I comment out the command line for each of the partitions, not changing where they mount, would that tell Linux not to mount them at all? or does fstab only apply to the drives showing up on the desktop?

Cheers,
Feck

---

### Post by Rui Pais on 2007-04-14
> **Feck said:**
> when trying your first method: gconf -editor

I get an error message saying the gconf command wasn't found

gconf-editor without the space
> 
About your second method, the editing of the fstab file

If I comment out the command line for each of the partitions, not changing where they mount, would that tell Linux not to mount them at all? or does fstab only apply to the drives showing up on the desktop?

No, linux would not mount them at all. You wouldn't access them until you mount it again. 
Thats why i suggest mount them anywhere else.

---

### Post by Feck on 2007-04-14
Thanks for the explanation, Rui! Everything's working as it should now :)

Cheers,
Feck

---

### Post by Rui Pais on 2007-04-14
great :)

have fun.

---

