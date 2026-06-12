---
title: "Problems with partitions"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-09-30
Hi, i can't re-size one of my partitions, Gparted says it's not un mounted..but it is! (help)

---

### Post by sab0403 on 2007-09-30
I've had the same problem with GParted and the Ubuntu LiveCD. The thing is, I've also had it with other Linux distros (SUSE 10 comes to mind). It's probably got something to do with either parted or mkfs (underlying commands).

The problem is that GParted actually does mount your partition after it does some work (after it deletes the partition, IIRC). What I've found you have to do is:

a) Be very quick to unmount as soon as GParted finishes an operation (by looking on the "advanced" or "expanded" section), or...
b) Do it by hand, with commands.

Sorry I can't be of more help. Good luck!

---

### Post by digital_exhaust on 2007-09-30
Try using the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php")... or you could use [PartedMagic]("http://partedmagic.com/index.html"), but either way I think you'll have better luck.

---

### Post by ajmannen on 2007-09-30
I don't have anny CD's available, how do you do it manually?

---

### Post by sab0403 on 2007-09-30
Use parted.

parted is a command line tool for managing partitions. I'm not sure what you need to rezise partitions safely, though. Let me search the net for a while.

---

### Post by sab0403 on 2007-09-30
Well, that was fast. According to the man, it's not that hard - you just use "rezise" from within the parted command line.

Basically, you go to a terminal, type *parted*, hit enter, and you'll get a command line in which to type the particular parted commands. The one you'll be using is *resize*.

Here's the man page on html:

[http://linux.die.net/man/8/parted](http://linux.die.net/man/8/parted)

---

