---
title: "Aldi / Lidi Photo Services Software."
date: 2013-10-02
forum: Any Other OS
---

### Post by leona on 2013-10-02
Hi.

Gosh that was hard work getting logged back on here, what a nightmare. anyhow.

I know I have now moved onto Linux Mint but as its based on Ubuntu I thought I'd ask my question here.

Has anyone tried to install the Photo software from the above supplier.

They have a Linux version, but when I install it, it complains about a missing shared library.
```

./Lidl-Photos UK: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
sudo apt-get install libstdc++6
libstdc++6 is already the newest version.

```
Any ideas?  
I am sure I had this working in Ubuntu 12.04, but no joy now.

---

### Post by howefield on 2013-10-02
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by sanderj on 2013-10-02
The Lidl program is 32-bit. Are you on 64-bit?

I am on 64-bit. I got this:

```
./Lidl-Photos UK: error while loading shared libraries: libgomp.so.1: cannot open shared object file: No such file or directory

```
After a
```
sudo apt-get install libgomp1:i386

```it worked.

HTH

---

