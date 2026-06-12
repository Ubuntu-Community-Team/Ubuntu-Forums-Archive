---
title: "Install GnuTLS"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-10-09
So, I'm attempting to compile the new version of FileZilla (3.0.1), and it requires a newer version of GnuTLS than there is in the repositories. This is the first time I've ever compiled anything from source.

In attempting to install the new version of GnuTLS, I'm compiling it as well. I have followed the following steps:

1. Download the archive from [ftp://ftp.gnutls.org/pub/gnutls/](ftp://ftp.gnutls.org/pub/gnutls/).
2. Extract archive and cd into its directory.
3. ./configure
4. make check install

I received the following error:

make[3]: *** No rule to make target `../libutils.la', needed by `hostname-check'.  Stop.

What can I do from here? If there's an easier way to install the new FileZilla, that would be wonderful, but it's interesting to try to learn to compile something.

Thanks.

---

### Post by Pumalite on 2007-10-09
Make sure you have:

sudo apt-get install build-essential

---

### Post by flamingsole on 2007-10-09
It says build-essential is already the newest version.

---

### Post by Pumalite on 2007-10-09
You have dependency problems then.

---

### Post by flamingsole on 2007-10-09
Meaning, I assume, that something that GnuTLS depends on is either missing or not as new as the version of GnuTLS I'm trying to install?

---

