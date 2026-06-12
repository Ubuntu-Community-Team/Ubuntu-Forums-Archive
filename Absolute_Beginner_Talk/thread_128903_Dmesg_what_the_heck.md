---
title: "Dmesg: what the heck?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by gigoguy on 2006-02-12
Hey all, newbie here trying to sort out some hardware issues while figuring out how diagnostics work in Linux.  As I understand it, dmesg is supposed to give me useful info about the state of my machine.  Instead I get this:

15099.277000] VFS: busy inodes on changed media.
[4515099.302000] VFS: busy inodes on changed media.
[4515101.334000] VFS: busy inodes on changed media.
[4515101.359000] VFS: busy inodes on changed media.
[4515103.392000] VFS: busy inodes on changed media.
[4515103.417000] VFS: busy inodes on changed media.
[4515105.449000] VFS: busy inodes on changed media.
[4515105.474000] VFS: busy inodes on changed media.
[4515107.506000] VFS: busy inodes on changed media.
[4515107.531000] VFS: busy inodes on changed media.
etc. for many lines

meep?
-confused newbie

---

### Post by bscbrit on 2006-02-12
The kernel is checking an item of removable media, such as a floppy disk, USB memory pen or such like, which appears to be missing but the kernel still has links to.  

I'm not sure but I suspect you removed a file system without unmounting it?

---

