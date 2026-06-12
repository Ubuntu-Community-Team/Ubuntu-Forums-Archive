---
title: "[SOLVED] moving mount points"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-02-16
I've got  dapper. edgy and fedora all on the same disk after some reading I wish I had made my mount points under /media/dapper instead of just /dapper. I've read the man mount and it shows how to move them, but it doesn't mention editing /etc/fstab afterwards. Will this happen automatically on reboot or do I need to do it myself?

---

### Post by milton1 on 2007-02-16
You will probably need to edit fstab manually.

---

### Post by taurus on 2007-02-16
If you change /dapper to /media/dapper in /etc/fstab, the next time you reboot, it will be mounted to /media/dapper automatically.

```
gksudo gedit /etc/fstab
```

---

### Post by rusty4r on 2007-02-16
> **taurus said:**
> If you change /dapper to /media/dapper in /etc/fstab, the next time you reboot, it will be mounted to /media/dapper automatically.

```
gksudo gedit /etc/fstab
```

So. one step instead of two Thats great. Thanks Taurus

I will have to create the directory first or will the directory be created automatically too?

---

### Post by taurus on 2007-02-16
You need to create it one time.

```
sudo mkdir /media/dapper
```

---

### Post by rusty4r on 2007-02-16
Thank you very much

---

