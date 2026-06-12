---
title: "Program for burning iso files"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-08-19
Hi.

I would like to know what program i should use, when i want to burn down Ubuntu Ultimate on a DVD so that i can boot from it ?

---

### Post by nitro_n2o on 2007-08-19
GnomeBaker burn on low speeds for good results.. better yet check the recommended speeds

---

### Post by trak87 on 2007-08-19
Do it from the terminal (command line):

```
growisofs -Z /dev/dvd=yourUbuntuDVD.iso
```

---

### Post by czepluch on 2007-08-19
> **trak87 said:**
> Do it from the terminal (command line):

```
growisofs -Z /dev/dvd=yourUbuntuDVD.iso
```

What will it do ?

---

### Post by Kilz on 2007-08-19
I am starting to like Brasero for burning cd/dvd's. You can install k3b but if you are running Ubuntu with gnome it installs a lot of files for kde.

---

### Post by trak87 on 2007-08-19
> **czepluch said:**
> What will it do ?

It will burn the Ubuntu iso image to a blank DVD.

---

