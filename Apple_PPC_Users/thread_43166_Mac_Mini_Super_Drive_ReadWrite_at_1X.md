---
title: "Mac Mini Super Drive Read/Write at 1X"
date: 2005-06-21
forum: Apple PPC Users
---

### Post by retart on 2005-06-21
I can't get my Mac Mini to read and write faster than 1x. It's prettyy slow. Does anyone know how to fix this? I've searched and couldn't find my answer. Thanks very much.

-Michael

---

### Post by Wombley on 2005-06-21
[QUOTE=retart]I can't get my Mac Mini to read and write faster than 1x. It's prettyy slow. Does anyone know how to fix this? I've searched and couldn't find my answer. Thanks very much.

-Michael[/QUOTE]

Just a guess (I don't have a mac mini), but many drive speed problems are resolved by running:

sudo hdparm -d1 /dev/dvd

To enable DMA on the drive.

---

