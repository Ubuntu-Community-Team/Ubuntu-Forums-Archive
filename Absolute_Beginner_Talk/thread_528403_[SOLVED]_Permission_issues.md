---
title: "[SOLVED] Permission issues"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by RonP on 2007-08-17
Ok i looked around for a fix in this forum i am sure it is here but i could not find it sorry.

I installed ubuntu over my mandriva spring installation 

i have hba1 and hda6 1 is the root folder and 6 is the home folder for the mandriva installation. Being i dumb dumb i figured i could access the hda 6 partition (mandriva's home with the ubuntu installation. Ican't

It says i dont have permissions.

Can someone walk me through fixing this or do i have to format all my music and pictures.

Thank you all for any assistance.

---

### Post by Hobo Joe on 2007-08-17
ALT + F2 will get you a run prompt. Type:
```

gksudo nautilus

```
That will get you a file browser with root privelages, but don't close it.

---

### Post by aysiu on 2007-08-17
In [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo mkdir /media/mandriva
sudo mount -t ext3 /dev/hda6 /media/mandriva
gksudo nautilus &
``` Press Control-L and type ```
/media/mandriva
```

---

### Post by RonP on 2007-08-17
ok thank you much

---

