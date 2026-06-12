---
title: "EXT2FSX with WRITE permission, possible?"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by volanin on 2008-04-27
Currently, I am running MacOSX Tiger 10.4.11, fully updated.
And my linux HOME partition is formatted with EXT2.

When I mount it under OSX using EXT2FSX, it always mounts with READ-ONLY permissions.
Is it possible to mount it READ-WRITE, to share the partitions between both systems?

Thank you!
:)

---

### Post by volanin on 2008-04-27
I found the answer for this buried deeply in a bug-report.
It seems that EXT2FSX has some incompatibilities with the EXT2 flag DIR_INDEX.

To enable write permissions in MACOSX, first you have to unset it:
**tune2fs -O ^dir_index [partition]**

Be aware though that EXT2FSX version 1.4D4 is unstable on the MACTEL.
Here, it crashed whenever you unmounted a read-write partition.
And that caused minor corruptions on the EXT2 filesystem.
:(

---

The bug report also states that it does not currently work in Leopard.
And I don't know if removing that flag is compatible with an EXT3 filesystem.

---

