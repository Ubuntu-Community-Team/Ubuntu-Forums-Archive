---
title: "Adept installation interrupted"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-29
I was installing Apache, PHP5 and MySQL together with Adept (Kubuntu 6.06)...all packages were downloaded properly... but then when the installation of those packages started.... a connection error popped up at about 50% and now I have a bunch of half-installed files like:

/etc/apache/httpd.conf.dpkg-inst.queue


Other than those... there were probably many others that didn't get installed at all.

I'm new so I don't know how to fix this. Is there anyway to get to the downloaded "packages" and "unpack" them to install the proper binaries?

I don't want to redownload 40M :\

---

### Post by dbd on 2006-11-29
I think if you use the command:
> sudo apt-get upgrade
then that will finish off any previously interrupted installs.

---

### Post by Verminox on 2006-11-29
Nah that won't help. The package has been downloaded so it shows status as "installed"... but it hasn't been upacked properly I guess so the binaries and other files arent' physically present in their respective directories.

---

### Post by Verminox on 2006-11-29
errrr...... any help?

---

