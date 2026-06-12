---
title: "Windows disk cannot be accessed for writing"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by shadowdance on 2007-08-28
Hey,

I have to authenticate myself to access my NTFS disk. Furthermore, I cannot access it read/write. I've been trying to configure fstab for it:

UUID=adb0b0ee-3ce9-43e7-bc99-98baab8d9ce3 none            swap    defaults,gid=0              0       0

...but whatever I write, nothing happens...

Why?

---

### Post by 505 on 2007-08-28
You need a special driver to write NTFS. It is called ntfs-3g. Install that and change the file type in fstab from ntfs to ntfs-3g.

---

### Post by Malta paul on 2007-08-28
Hi 
Here are a couple of links that may help you:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

If you still have problems I will try to explain, but these links explain rather better than I can!

Good luck:wink:

---

