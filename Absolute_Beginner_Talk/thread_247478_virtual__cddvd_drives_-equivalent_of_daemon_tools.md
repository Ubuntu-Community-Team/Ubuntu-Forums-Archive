---
title: "virtual  cd/dvd drives -equivalent of daemon tools?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-30
Hi,
Is there any software out there that will let me mount a cd image to a virtual drive in ubuntu?

thanks in advance!

---

### Post by Bachstelze on 2006-08-30
No need for any extra program, the feature is already built in the kernel. Run

```
sudo mount /path/to/file.iso /path/to/mountpoint
```

---

### Post by christhemonkey on 2006-08-30
> **HymnToLife said:**
> No need for any extra program, the feature is already built in the kernel. Run

```
sudo mount /path/to/file.iso /path/to/mountpoint
```

Do you not need to specify options with that command?:

```
sudo mount -t iso9660 -o loop /path/to/file.iso /path/to/mountpoint 
```

---

### Post by furiousV on 2006-08-30
> **HymnToLife said:**
> No need for any extra program, the feature is already built in the kernel. Run

```
sudo mount /path/to/file.iso /path/to/mountpoint
```

Haha, thats just amazing!

Usually when you mount, it automatically uses the best filesystem it thinks it is, right?

---

### Post by bplus on 2006-08-31
superb, wonder how many image types it supports e.g. mds, nrg etc?

---

### Post by xfred on 2006-09-03
Brilliant... and perfect timing, as I was just looking for this :)

---

### Post by gynther on 2006-09-03
> **bplus said:**
> superb, wonder how many image types it supports e.g. mds, nrg etc?

It think it only supports .iso natively. According to [this]("http://gentoo-wiki.com/TIP_Mounting_Iso_Files") page in the Gentoo wiki there are applications that convert .mdf and .nrg files to .iso for you. Have **not** tested them so I don't know how well they work.

If I remember there was also a kernel module project that made .nrg support in the kernel native, but I can't seem to find that project.

---

