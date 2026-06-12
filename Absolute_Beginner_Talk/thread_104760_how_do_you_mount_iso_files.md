---
title: "how do you mount iso files?"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-16
Not burn, but mount the iso's themselves.

---

### Post by psusi on 2005-12-16
Associate a loopback device with the file and mount it.  Mount can do this for you, and I think the syntax is:

mount -t iso9660 -o ro,loop /foo.iso /mnt

Otherwise you can use losetup to tie a loopback device to the file, then mount that loopback device just like you would the cd.

---

### Post by akvik on 2005-12-16
[http://www.ubuntuforums.org/showthread.php?t=87369](http://www.ubuntuforums.org/showthread.php?t=87369)

:-)

---

