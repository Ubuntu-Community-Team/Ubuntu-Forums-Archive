---
title: "Virtual Drive Software?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by StopTheOncoming on 2007-10-22
I was looking for a program that could allow me to create virtual drives and emulate .iso images like DAEMON Tools or Alcohol 120%. I wanted this so I could install Ubuntu Studio. If anyone could point me in the right direction, I would be very grateful.

Thanks!

---

### Post by hyper_ch on 2007-10-22
you don't need any special software. You can mount iso images just like that.

---

### Post by roger99 on 2007-10-22
> **StopTheOncoming said:**
> I was looking for a program that could allow me to create virtual drives and emulate .iso images like DAEMON Tools or Alcohol 120%. I wanted this so I could install Ubuntu Studio. If anyone could point me in the right direction, I would be very grateful.

Thanks!

Are you allready running ubuntu of some flavour?

If so you can just add the ubuntu-studio repo and then in synaptic install all ubuntu-studio packages

EDIT:  Try following instructions after the link

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

---

### Post by djnapster on 2007-10-28
> **hyper_ch said:**
> you don't need any special software. You can mount iso images just like that.

How can i mount them?

---

### Post by hyper_ch on 2007-10-28
```

sudo mount -o loop -t iso9660 path/to/file.iso /path/to/mounting/point

```

---

