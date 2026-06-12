---
title: "why can't I go to my floppy ?"
date: 2005-06-19
forum: Absolute Beginner Talk
---

### Post by ness07 on 2005-06-19
I'm a newbaby, and recently I load ubuntu live cd in my dell 8250.  All things it´s ok, but I don't see my floppy disk, nor any floppy icon in my desktop. Anybody could help me? ](*,)

---

### Post by Zelut on 2005-06-19
[QUOTE=ness07]I'm a newbaby, and recently I load ubuntu live cd in my dell 8250.  All things it´s ok, but I don't see my floppy disk, nor any floppy icon in my desktop. Anybody could help me? ](*,)[/QUOTE]
 media devices (hard drives, floppies, cd's, etc) all need to be mounted under linux.  I'm not sure but the live CD may not mount those by default so you may need to do it manually.  You'll need to find the right /dev where your floppy is listed (probably fd/ or fd0/ and 'mount' that.

sudo mount <dev> <location>

for example I mount my windows partition at /mnt/windows/ so I would type

sudo mount /dev/hda5 /mnt/windows

at this point you can cd to your location & find the files on floppy.

Hope this helps.

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=ness07]Anybody could help me? ](*,)[/QUOTE]

Sure. The best way is to go to "Computer" under the "Places" menu option.

Then click on the floppy icon.

---

