---
title: "Making a sep home partition - which files to backup - just in case disaster?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-03
I've so far backed up my home folder,

copy of sources.list and  --get-selections | grep -v deinstall > ubuntu-packages which creates a list of installed packages.

Anybody think of any other stuff to backup?

---

### Post by hyper_ch on 2007-10-03
/home and /etc should be sufficient... if you have websites under /var/www you should also backup that and the default installation path for mysql dbs is /var/lib/mysql, so in case you use them, you should also backup that....

---

### Post by philinux on 2007-10-03
Cheers thanks for reply - whats in etc.

and can you just copy it back following a re-install should that be necessary.

---

### Post by chrismine on 2007-10-03
Try this link - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

It worked for me!

---

### Post by philinux on 2007-10-03
Thats what I'm going to do after I've backed up essentials.

---

