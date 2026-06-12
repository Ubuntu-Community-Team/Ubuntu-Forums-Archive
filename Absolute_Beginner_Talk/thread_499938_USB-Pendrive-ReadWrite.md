---
title: "USB-Pendrive-Read/Write"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by rafaelxy on 2007-07-13
I use Ubuntu 7.04.

When I plugged my pendrive, the system mount it automatically, but I can't write/change ANYTHING.

How can I make to the system mount any stuff (pendrive, NTFS hard drivers) automatically in read-write mode?

---

### Post by JTux on 2007-07-13
What is the filetype of your USB-pendrive?

To check, plug the device and type this command in a terminal
```
grep USB /etc/mtab | grep ntfs
```

if it is not NTFS you will just see the prompt

If it is NTFS follow this howto 
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

You will have to select"Enable Write support for external device"

---

