---
title: "Reinstalling OSX on single boot macbook"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by capawi on 2008-08-26
I am currently single booting ubuntu 8.04 on my macbook v1 but would like to install osx again but the installation disc will not allow this it says my harddrive cannot be install to. is this a known problem?

Help would be greatly appreciated

Carl

---

### Post by WRDN on 2008-08-26
> **capawi said:**
> I am currently single booting ubuntu 8.04 on my macbook v1 but would like to install osx again but the installation disc will not allow this it says my harddrive cannot be install to. is this a known problem?

Help would be greatly appreciated

Carl

Boot from the a LiveCD, and open the partition editor. Delete any partitions you no longer want (e.g. swap) and format the space to hfs+.
Now try to install OSX again, and it should recognize the drive and a compatible file system.

---

### Post by cyberdork33 on 2008-08-26
> **capawi said:**
> I am currently single booting ubuntu 8.04 on my macbook v1 but would like to install osx again but the installation disc will not allow this it says my harddrive cannot be install to. is this a known problem?

Help would be greatly appreciated

Carl
When you boot the OS X install dvd, you need to start disk utility and repartition / format the drive from scratch.

---

