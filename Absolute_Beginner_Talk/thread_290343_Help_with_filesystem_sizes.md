---
title: "Help with filesystem sizes"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by deep.tinker77 on 2006-11-01
Hello all, I used Gparted to create a partition after my install of ubuntu, the only thing is that I can't add that space to my /dev/sda2. The reason I'm trying to do this is because it's only about 6GB in size, and I've downloaded Automatix2 and if I want to install the majority of packages with it, i'm going to run out of room. Gparted won't allow me to grow my original partition that linux was installed on. Is there any way to do this without doing a complete re-install of linux? Thanks for any help anyone may have.

---

### Post by Sef on 2006-11-01
Are you using the latest version of GParted?

---

### Post by deep.tinker77 on 2006-11-01
Yes, the latest version that was available on the website.

---

### Post by CatKiller on 2006-11-01
> **deep.tinker77 said:**
> Gparted won't allow me to grow my original partition that linux was installed on.

GParted won't let you do this **while that partition is mounted**. You can use a live cd environment to do things while that partition is unmounted. You can use the Ubuntu live cd to do it, but if you want to move the **start** of your ext3 partition, you'll want to use the GParted live cd.

---

