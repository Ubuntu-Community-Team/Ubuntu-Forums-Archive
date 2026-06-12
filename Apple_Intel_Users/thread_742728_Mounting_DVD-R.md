---
title: "Mounting DVD-R"
date: 2008-04-02
forum: Apple Intel Users
---

### Post by omax on 2008-04-02
I have a burnt DVD-R that I got on the snailmail from a friend.

I don't know how it's burnt, but it contains data-files (.avi, .txt etc)

When I try to mount it in Xubuntu ( 2.6.22-14-generic ):
```

n1mda@royal:/media$ mount cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
```

n1mda@royal:/media$ sudo mount -t udf /dev/scd0 cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
```

n1mda@royal:/media$ dmesg|tail
[  847.628000] UDF-fs: No fileset found
[  847.692000] Unable to identify CD-ROM format.

```

I have yet not found a solution on google - anyone have any ideas?

Free hugs for everyone that answers!
Appreciate your help :)

---

### Post by cyberdork33 on 2008-04-02
I'd say you need to figure out how he burned it... Was it created on a Mac? Can't you make a HFS formated optical disc?

---

### Post by omax on 2008-04-03
> **cyberdork33 said:**
> I'd say you need to figure out how he burned it... Was it created on a Mac? Can't you make a HFS formated optical disc?

I forgot to mention, that it was burnt in Windows, and it mounts fine there.

It does mount in MacOSX - but it appears to be empty (unburnt)

---

### Post by cyberdork33 on 2008-04-03
sounds like he didn't close the disc or something. I think your best bet is to use a windows machine to get the files off the disc onto something that you can use under OSX / Ubuntu. (It might work under a VM too...) Sorry I can't help more.

---

### Post by omax on 2008-04-03
It does work under a VM if I mount /dev/scd0 - it was just for further fixes I thought it might be a Ubuntu specific problem.

I've seen a lot of posts like this, but no solution, perhaps this is the ONLY option.

Thank you cyberdork33 for your help!

---

