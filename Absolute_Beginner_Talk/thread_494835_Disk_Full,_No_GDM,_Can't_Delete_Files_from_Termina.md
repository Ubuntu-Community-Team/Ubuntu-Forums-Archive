---
title: "Disk Full, No GDM, Can't Delete Files from Terminal"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Aktrop on 2007-07-07
Hi -

I tried backing up my work to my external hard drive, but it seems that instead it all went to /var/backup/

As a result, my hard drive is now totally full which I checked via df -h and I can't log into GDM. Now when I try to delete the contents of /var/backup/ with sudo rm -rf ~/.backup/* the command goes through but du -h shows that the offending files are still there. And of course, I can't log into GDM.

Can someone please tell me where to go from here?

Thanks,

Aktrop

---

### Post by taurus on 2007-07-07
Try

```
sudo rm -rf /var/backup
df -h
```

---

### Post by Aktrop on 2007-07-07
It worked!!!


Thanks you thank you thank you thank you!!!!!!!!


You ROCK!!

---

