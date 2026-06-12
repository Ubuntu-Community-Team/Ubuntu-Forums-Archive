---
title: "Need to make a SGD disk"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by xintol on 2007-05-03
Hello All, I would like to make a Super Grub Disc in a floppy. What software or method can I use to copy the *.img file to floppy.  Thanks.

---

### Post by steve.horsley on 2007-05-03
Use dd. This is part of the default install.
**sudo dd if=whateverItIs.img of=/dev/fd0**

---

### Post by louieb on 2007-05-03
Copy to a floppy example 

Linux users run the dd command and optionally the compare command.[LIST]
[*]change to the directory holding sbootmgr.dsk
[*]dd if=sbootmgr.dsk of=/dev/fd0
[*]cmp  sbootmgr.dsk /dev/fd0[/LIST]
See [Nuts on SmartBootManager]("http://louboldt.com/ilinuxsbm.htm") for an eample of how to do it in windows.

---

