---
title: "ejecting cd"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by fminmexico on 2007-12-17
I use Mac and Ubuntu on my Mini I inserted a mac disc by mistake and Ubunto could not read it.Nothing appears on my desktop in the disc manager it lists what it is and says inaccessible.How do I eject this disc.I have tried everywere to eject it no luck.I have no  problems with any other cd.
    fminmexico.

---

### Post by jken146 on 2007-12-17
```
sudo umount /dev/cdrom0 && eject /dev/cdrom0
```

---

### Post by fminmexico on 2007-12-17
> **jken146 said:**
> ```
sudo umount /dev/cdrom0 && eject /dev/cdrom0
```

I pasted this in the teminal and I got not found.
      fminmexico.

---

### Post by chamberlain2006 on 2007-12-17
Simply typing "eject" should do it.  (Without quotes of course)

---

### Post by fminmexico on 2007-12-17
> **chamberlain2006 said:**
> Simply typing "eject" should do it.  (Without quotes of course)

Tried that nothing happens.
  fminmexico.

---

