---
title: "Tarballs are beyond me"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Andre_3608 on 2007-10-28
I have downloaded striata-reader.tar.gz to my desktop - but have not a clue how to proceed.  Elementary, apparently - but not for me!  Would some kind soul please assist this ignoramus?

---

### Post by Shazaam on 2007-10-28
This might help...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by kellemes on 2007-10-28
Ignoramus? :lolflag:

---

### Post by aysiu on 2007-10-28
Tarballs are beyond me, too.

Try pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install install alien
wget -c http://www.striata.co.za/products/downloads/striata-reader-1.0-27-linux-2.4-intel.rpm
sudo alien -i striata-reader-1.0-27-linux-2.4-intel.rpm
```

---

