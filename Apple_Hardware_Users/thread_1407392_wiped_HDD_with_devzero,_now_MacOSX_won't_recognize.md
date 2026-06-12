---
title: "wiped HDD with /dev/zero, now MacOSX won't recognize it"
date: 2010-02-15
forum: Apple Hardware Users
---

### Post by itdoesnot on 2010-02-15
my girlfriend has an old ibookG4 she wants to sell and so asked me
to wipe the hard drive, i remembered seeing some dd tutorials and remember
thinking it was easy, so i booted ubuntu 9.04 live-ppc  and ran
one pass of dd if=/dev/urandom and one of /dev/zero
i figure this is safe enough since she doesn't really keep nuclear codes or anything

she can't sell it with ubuntu ,which DOES install and recognize HDD because most people expect a Mac to have OSX. the fact that i prefer linux is besides the point.   
we do have the original restore discs and booting from it  works fine up to the point where disk utility asks where to install, there is no drive recognized.

i read some post somewhere that said that if the drive is formatted as FAT32 then disk utility will recognize it and reformat as hfs+. i used fdisk , and mkfs but, it didn't work
i read at another site that installing any OS would fix it (fix MBR, etc..) so i installed ubuntu, and tried again to boot and install OSX only to find the same problem.

i'm just about out of ideas, and i'm just kicking myself because i just found out disk utility has it's own 'zero fill' features i could have used and saved myself the 8hr /dev/urandom pass. not to mention the fact that i've created a problem rather than solved one.

(OSX 10.3 by the way)

---

### Post by linuxopjemac on 2010-02-15
why don't you fill the HD with zero's from the OSX cd now and then try to reformat ? Or is the drive not seen at all by the Disc Utility?

---

### Post by samarium on 2010-02-15
what about trying parted?

it seems you should be able use the mklabel command to create a mac label

then you should be able to build a hfs partition

write that out and exit parted

and then do use mkfs.hfsplus to create a mac file system

---

### Post by linuxopjemac on 2010-02-15
good idea samarium:
[http://www.gnu.org/software/parted/manual/html_node/mklabel.html](http://www.gnu.org/software/parted/manual/html_node/mklabel.html)

---

### Post by itdoesnot on 2010-02-15
thanks everybody, i'll try parted when i get back from school
and post my results

---

### Post by itdoesnot on 2010-02-16
it almost worked, except that ubuntu 9.04 ppc live doesn't come
with mkfs.hfsplus (at least not in /sbin) and the ibookG4 won't boot 9.10
does anyone know of anything like parted magic or ubuntu rescue for ppc?

---

### Post by itdoesnot on 2010-02-16
ok, i've found something called PPCRCD
[http://ppcrcd.pld-linux.org/](http://ppcrcd.pld-linux.org/)  and it comes with pdisk
which is OSX's commandline partitioning tool
hopefully this will work

---

