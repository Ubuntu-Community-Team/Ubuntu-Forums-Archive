---
title: "Xubuntu: How to find the floppy drive in Abiword?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by Nostromo on 2006-02-21
I'm definitely a beginner, so I'm gonna need some simple advice on certain subjects my new Xubuntu (XFce). First one is about Abiword.

How do I find the floppy drive? When saving or opening, the program offers a big list of folders, but I couldn't tell if one of them refers to the floppy drive. Under 'File System' there is a folder called 'dev' where there seems to be cdrom.

Probably I will need a lot advice in the future, but I thought I'd start by studying the everyday things first, before going deeper. Before this I have superficial experience only on Win95...

---

### Post by jorn on 2006-02-21
Try> filemanager. Open fstab. Further down /media/floppy0.
-Jorn-

---

### Post by Schmots on 2006-02-21
Automount does not always work, that may be why you don't see the floppy in /media/floppy0

Try 

mount /media/floppy0

when you put the floppy disk in, just besure to 

umount /media/floppy0

before you eject the floppy

---

