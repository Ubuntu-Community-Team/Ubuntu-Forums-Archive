---
title: "rar problem"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by SiriusTux on 2007-08-06
I just installed rar 3.70, everything seems to be good, bu when I try to execute rar command I get:

rar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by rar)

I use Ubuntu 6.06 LTS.....
I tried to find something around here but I can't find any solution.
Could someone help me?

Thank you....

Sirius

---

### Post by por100pre1 on 2007-08-06
I think you need **libc6**, however I'm not sure about it...

---

### Post by SiriusTux on 2007-08-06
libc6 is already installed on the system....and seems to work fine.

Thank you

Sirius

---

### Post by milosz.galazka on 2007-08-06
Try this [http://forums.debian.net/viewtopic.php?t=13957&postdays=0&postorder=asc&start=20&sid=6426819a26976fe50ad8cb8fcd1d6ad9](http://forums.debian.net/viewtopic.php?t=13957&postdays=0&postorder=asc&start=20&sid=6426819a26976fe50ad8cb8fcd1d6ad9)

Or maybe this will help: [http://forums.debian.net/viewtopic.php?p=62383](http://forums.debian.net/viewtopic.php?p=62383)

---

### Post by atomkarinca on 2007-08-06
if you're using it as ./rar then try ./rar_static

---

### Post by SeanHodges on 2007-08-06
I might be missing something here, but couldn't you install unrar from the package manager? is there an advantage of building a specific version from source?

More curious, I don't have an answer to the problem sorry.

---

### Post by SiriusTux on 2007-08-07
Thank you everyone
I solved installing rar 3.60 instead of 3.70 (that is the release that you can find at this moment at [http://www.rarlab.com](http://www.rarlab.com))

:):):):):):):)

---

### Post by asmoore82 on 2007-08-07
you are only planning on using it to extract rar archives; not to create new ones right?

you can already right click and "create archive" out-of-the-box.

*.tar.gz is the UNIX archive format that will be universally usable on every *NIX system.

---

### Post by SiriusTux on 2007-08-07
Right!!
I know and Ius tar.gz.....

---

