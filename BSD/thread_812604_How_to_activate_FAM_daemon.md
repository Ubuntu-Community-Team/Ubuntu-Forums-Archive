---
title: "How to activate FAM daemon?"
date: 2008-05-30
forum: BSD
---

### Post by techmarks on 2008-05-30
I've installed XFCE4 on FreeBSD 7.0.

Everything looks good execept file changes don't update on the desktop.

I think this must be because XFCE4 uses FAM (File Alteration Monitor) to track file changes and it's not being activated.

I tried putting the following line in /etc/rc.conf

fam_start = "YES"

but that didn't help at all.

Does anyone know how to activate FAM on FreeBSD 7.0 to work with XFCE4?

I did compile FAM from the ports already.

Thanks for any info.

---

### Post by cardinals_fan on 2008-05-30
Check out [http://sourceforge.net/projects/bsdfam:](http://sourceforge.net/projects/bsdfam:)

> BSD-licensed clone of SGI's FAM (File Alteration Monitor) API used to notify application when specific files or directories are changed. Unlike Linux version, to monitor changes it uses excellent kqueue(9) kernel API available in modern BSD derivatives.

---

