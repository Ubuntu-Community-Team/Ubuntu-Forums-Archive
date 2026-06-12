---
title: "How do i get read access to my CDROM's mount point?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-08-01
I'm on my main account so shouldn't I automatically have access? Yet when I use this code:

```

ln ~/.wine/dosdevices

ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
ln -s /mnt/cdrom ~/.wine/dosdevices/d\:

```

This comes up...

```

charco@charco-desktop:~$ ln ~/.wine/dosdevices
ln: `/home/charco/.wine/dosdevices': hard link not allowed for directory
charco@charco-desktop:~$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
charco@charco-desktop:~$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
ln: creating symbolic link `/home/charco/.wine/dosdevices/d::' to `/dev/hdc': File exists
charco@charco-desktop:~$ ln -s /mnt/cdrom ~/.wine/dosdevices/d\:
ln: creating symbolic link `/home/charco/.wine/dosdevices/d:/cdrom' to `/mnt/cdrom': Permission denied

```

How do I get write access or whatever?

---

### Post by professor_chaos on 2006-08-01
your problems stem from the fact that your trying to link to d: which already exists. Either remove d: or make a different link ( ie zz: )

---

### Post by Charco on 2006-08-01
Brilliant! Thanks! You rock!

---

