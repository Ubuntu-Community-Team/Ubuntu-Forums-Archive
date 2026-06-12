---
title: "Dual Boot Problem"
date: 2012-09-23
forum: Apple Hardware Users
---

### Post by zancudo on 2012-09-23
Hallo,

About one month ago i turned my Macbook2,1 to dual boot Mac OS X (Snow Leopard) and Trisquel 5.5 which is a 100% free software Linux distro based on Ubuntu 11.10.
[http://trisquel.info/en](http://trisquel.info/en)

I use refit 0.14 which allows to boot into Mac OS X or Trisquel.
Choosing Triquel forwards to a Grub2 Boot Loader. all works well... untill today when Trisquel all out of a suddon didnt boot anymore. it seemed to me that the grub2 boot loader did not even start. but i can't say that for sure, because i did hide the menu.

after hours of fiddeling with various tools (gdisk, gptsync) i managed to be able to boot Trisquel again. but something is still odd: both, the gptsync coming with refit and that in Trisquel which is the version 0.14-2(ubuntu) say that they cannot sync the mbr and the gpt:

```

sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    171682495  Mac OS X HFS+
 3      171682496    248116089  Unknown
 4      248116090    250069215  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2             40       409639  0b  FAT32 (CHS)
 3         409640    171682495  af  Mac OS X HFS+
 4 *    171682496    248116089  83  Linux

Status: GPT partition of type 'Unknown' found, will not touch this disk.

```The entry 3 in the GPT was set by gdisk via MacOSX with partition type 8300 which is "Linux filesystem".

What is broken with the tables? How can i repair that?

Also i am not sure whether the boot flag in the MBR is set correctly.

More strange, the refit menu now has two menu entrie for booting Linux, both working. how can i safely remove one of them?

thanks in advance!

---

### Post by proycon on 2012-09-23
The partitions tables are indeed out of sync. You said you managed to boot into Linux again? Then install the latest gptsync and run that (compile and install from source if necessary). There was an issue with recognising certain partitions (including dedicated grub partitions) in older versions, the one in your distro and in reFIt is probably too old?

---

### Post by zancudo on 2012-09-24
thank you.

could you explain to me please how you notice that the tables are out of sync?

the hard disk has 4 partition i believe:
1 EFI
2 Mac OS X
3 Linux System
4 Linux Swap

---

