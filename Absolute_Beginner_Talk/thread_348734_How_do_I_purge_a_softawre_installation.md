---
title: "How do I purge a softawre installation"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-01-29
I messed up an installation of MediaWiki 1.5 and it is preventing Apache2 from loading, creating this error:

"grep: /etc/apache2/sites-enabled/001-mediawiki: No such file or directory [fail]"

How do I purge my system of all traces of MediaWiki (I used synaptic and still get this message)

Thanks in advance...

---

### Post by n8bounds on 2007-02-25
Be root then look in that directory (/etc/apache2/sites-enabled/) and remove the simlink with mediawiki in its name.

---

