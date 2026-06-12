---
title: "tat/gzip for DOS?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by ssalman on 2006-04-24
I'm looking for a tar/gzip utilities for DOS that are compatibale with Linux. I looked at [www.gzip.org]("http://www.gzip.org") & [http://unxutils.sourceforge.net]("http://unxutils.sourceforge.net") but the z option to compress the tar file using the tar command was not supported. I know it exists as I used to have it on my USB key, but it went bad and I lost all my files with it, and now I can't remember where I got it from :(. Does anyone know where to get this?

I want to use the following command:

tar cvzf c:\test.tgz C:\DIR

Thanks.

---

### Post by cgjones on 2006-04-24
Check out [7-Zip]("http://www.7-zip.org/"). They have a command line version available. I've only used the GUI version, but it supports .tar, .gz, and others.

---

### Post by ssalman on 2006-04-24
Thanks cgjones, but I would prefer GNU tar/gzip... I will give 7z a try though. Thanks.

---

### Post by ssalman on 2006-04-25
found it... at [http://gnuwin32.sourceforge.net/](http://gnuwin32.sourceforge.net/)

bsdtar will do the trick.... thanks.

---

