---
title: "psp file transfers"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-09-27
how do i transfer a file to my PSP?
i tryed drag and drop but that does not work.

---

### Post by zith on 2005-09-27
This is what i mount my psp with (with the usb cord, that is);

From fstab:
```

/dev/sda1       /media/psp      vfat    noauto,defaults,user,sync,shortname=winnt,noexec,nosuid,nodev,quiet     0       0

```

This works fine for me, the psp auto-mounts in /media/psp and all is good.

---

### Post by jasonpeinko on 2005-09-27
so i just type that? and then what?

---

### Post by TristanMike on 2005-09-27
I would assume he would want you to copy/paste that into your fstab file /etc/fstab, save, and try the PSP. If you're looking for the files or where to put them, in this case it seems to be /media/psp.

---

