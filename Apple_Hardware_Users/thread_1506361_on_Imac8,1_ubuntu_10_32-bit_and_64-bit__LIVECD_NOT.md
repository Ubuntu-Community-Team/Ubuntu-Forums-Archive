---
title: "on Imac8,1 ubuntu 10 32-bit and 64-bit  LIVECD NOT LOADING!! plz help"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by johntkucz on 2010-06-10
Hello,

Trying to boot ubuntu 10.04 off imac8,1.  I downloaded and burned 32-bit and 64-bit copies of the OS and when I "c-key boot" on the imac with the livecd all I get is a blinking underscore hashmark and then I have to hard restart the computer.

The ubuntu livecd boots fine in macbook pro.

Please help. Thanks.

Highly vexed at moment.:mad::mad::confused::confused:


(btw, [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac) is useless because that guide treats livecd-booting as a breeze.  Tha's what isn't functioning at moment).


additionally, when I try to format partitions


diskutil resizeVolume /dev/disk0s2 71.1G Linux Linux 25G "MS-DOS FAT32" Windows 15G

"linux" isn't a recognized filesystems format.  which should I use (ext3/4 isn't listed as filesystems either)

---

### Post by linuxopjemac on 2010-06-10
You could try booting with a boot option (e.g. acpi=off), see [here]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Regunirun on 2010-06-10
I have the same model iMac. 

I have noticed the same problem.

I do however happily tripleboot W7, Lucid, and SnoLeo.

I could not figure out a solution to why the blinkdeath occurs. However, if you try booting into OS X, then holding "alt" at restart, it should work. Sometimes it works, sometimes it doesn't. I have no idea, all I know is that I had the same problem, still do, and the solution is repetition.

Hope this was of some help ;)

---

